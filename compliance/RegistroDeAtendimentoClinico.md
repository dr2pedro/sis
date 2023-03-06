## Registro de Atendimento Clínico 
**Fonte**: [PORTARIA Nº 234, DE 18 DE JULHO DE 2022](https://www.in.gov.br/en/web/dou/-/portaria-n-234-de-18-de-julho-de-2022-416506215)

<br>

|||
|:-------------:|:------------|
|  **Autores**  | [Pedro Paulo dos Santos](https://github.com/dr2pedro), [Felipe Lima](), [José Antonio Hojota]() e Lorena Martins |
| **Criado em** | 05-03-2022 |

<br>

### Índice

- [Resumo](RegistroDeAtendimentoClinico.md#resumo)
- [Motivacao](RegistroDeAtendimentoClinico.md#motivação)
- [StakeHolders](RegistroDeAtendimentoClinico.md#stakeholders)
- [Especificação](RegistroDeAtendimentoClinico.md#especificação)
    - [Identificação do Indivíduo](RegistroDeAtendimentoClinico.md#identificacão-do-indivíduo-obrigatório-único-objeto)
        - [Identificador Demográfico](RegistroDeAtendimentoClinico.md#identificador-demográfico-opcional-único-object-validação)
    - [Caracterização do Atendimento](RegistroDeAtendimentoClinico.md#caracterizacão-do-atendimento-obrigatório-único-objeto)
        - [Profissionais do Atendimento](RegistroDeAtendimentoClinico.md#profissionais-do-atendimento-obrigatório-único-object)
            - [Profissional](RegistroDeAtendimentoClinico.md#profissional-obrigatório-múltiplos-object)
    - [Motivo do Atendimento](RegistroDeAtendimentoClinico.md#motivo-do-atendimento-opcional-único-objeto)
    
<br>

### Resumo

### Motivação

Os sistemas de informação em saúde (SIS) disponíveis no mercado atualmente abordam o cuidado em saúde como um sistema de histórico de cuidado, excluindo a perspectiva centrada no paciente, desconsiderando sua segurança e seus direitos, sem qualquer cuidado com os dados produzido no atendimento e impedindo a interoperabilidade com outros atores do sistema.

Os profissionais que utilizam esses sistemas na maioria das vezes são obrigados a registrarem diversas entradas manualmente, duplicado informações já registradas por colegas que atenderam o paciente anteriormente.

Os gestores de estabelecimentos de saúde dependem de mapeamentos personalizados para emitir relatórios compilados dos cuidados prestados pela sua unidade.

Com a implementação do padrão, previsto em lei, do Registro de Atendimento Clínico (RAC) será possível gerenciar o cuidado focado no paciente, permitir que o profissional de saúde tenha acesso a informações previamente fornecidas pelo paciente aos profissionais anteriores, reduzir a inserção manual de dados não padronizados e permitir que os registros sejam compilados de forma a facilitar a emissão de relatórios.

<br>

### StakeHolders

Os atores mencionados na lei como partes interessadas na implementação do Registro de Atendimento Clínico são:

1. Profissionais de saúde de atendimentos ambulatóriais e aqueles venham a atender o paciente em regime de urgência/emergência;

2. Estabelecimentos de saúde;

3. HealthTechs;

4. Gestores e especialistas clínicos (_escopo aberto_), _i.e._ coordenadores regionais de saúde da mulher ou saúde da criança;

5. Entidades representativas dos usuários do serviço de saúde, _i.e._ comissão de saúde;

6. Especialistas de linhas de cuidado do indivíduo (_escopo fechado_), _i.e._ o reumatologista da paciente;

7. O próprio paciente e/ou seus responsáveis (_escopo aberto_);

<br>

### Especificação

O Registro de Atendimento é um agregado, bem ao estilo *Domain Driven Design*, de **onze** outros objetos principais:

1. Identificação do Indivíduo;
2. Caracterização do atendimento;
3. Motivo do atendimento;
4. Observações;
5. Problemas / diagnósticos avaliados;
6. Alergia e/ou reação adversa;
7. Procedimento(s) realizado(s) ou solicitado(s);
8. Prescrição no atendimento;
9. Plano de cuidados, instruções e recomendações (na alta);
10. Dados do desfecho;
11. Informações Adicionais;

Repare que esse agregado herda vários identificadores únicos de seus objetos de construção tais como: identificação do indivíduo, endereço, data e hora do atendimento e etc... O conjunto desses identificadores o torna único podendo ser considerado em si uma entidade/objeto de domínio, devendo ao menos ser persistindo em repositório próprio.

<br>

**Vale lembrar que esta lei não menciona o prontuário, apenas o RAC.**

<br>

#### Identificacão do Indivíduo [*obrigatório*, *único*, *objeto*]

Para identidicação do indivíduo apenas o CPF ou Carteira Nacional de Saúde (CNS) e o endereço. Caso o paciente não possua CPF e CNS, deve-se inserir um conjunto de dados demográficos.

1. **Identificador Nacional** [*obrigatório*, *único*, *string*, *validação*] - Numeração do CPF ou da CNS;

|||
|:----------------|:---------|
| **Validação**   | Em caso de CPF, consultar se existe a CNS, caso não deve ser criada. |

2. **Identificador Demográfico** - Um outro objeto contendo os dados demográficos requeridos.

|||
|:----------------|:---------|
| **Validação**   | Apenas inserido na ausência do Identicador Nacional. |

3. **Endereço** [*opcional*, *único*, *Array<string>*, *validação*] - Uma sequencia contendo os nomes do logradouro em ordem de precedência.

|||
|:----------------|:---------|
| **Validação**   | Apenas inserido caso a primeira ocorrência (país) seja Brasil. |

**Obs-1**.: Em um sistema geolocalizado a referência dessas strings define objetos geojson agregados em si, consultar [tesa - tools for easy spatial analysis](https://github.com/CodePlayData/tesa).

<br>

##### Identificador Demográfico [*opcional*, *único*, *object*, *validação*]
Para se idenficar o indivíduo por dados demográficos deve-se ter:

1. **Nome Completo** [*obrigatório*, *único*, *Array<string>*];
2. **Nome Social** [*opcional*, *único*, *Array<string>*];
3. **Nome completo da mãe** [*obrigatório*, *único*, *Array<string>*];
4. **Data de nascimento** [*obrigatório*, *único*, *string*, *validação*]

|||
|:----------------|:---------|
| **Validação**   | Compliance a ISO 8601. |

5. **Sexo** [*obrigatório*, *único*, *enum*];
6. **País de Nascimento** [*opcional*, *único*, *enum*];
7. **Município de Nascimento** [*opcional*, *único*, *enum*];

**Obs-2**.: Os enums geográficos podem vir da classificação oficial do IBGE.


<br>

#### Caracterizacão do Atendimento [*obrigatório*, *único*, *objeto* ]

Um atendimento é composto de:

1. **Identificador do Estabelecimento de saúde** [*obrigatório*, *único*, *string*] - O Cadastro Nacional de Estabelecimento em Saúde (CNES) de onde o atendimento está sendo produzido;

2. **Procedência** [*obrigatório*, *único*, *enum* ] - Identifica o serviço que encaminhou o indivíduo ou a sua iniciativa/de seu responsável na busca pelo acesso ao serviço de saúde. {*Ordem Judicial*, *Retorno*, *Demanda espontânea*, *Demanda Referenciada*};

3. **Identificação da equipe de saúde** [*opcional*, *único*, *enum* ] - Número válido do Identificador Nacional de Equipe (INE) no CNES;

4. **Data e hora do atendimento** [*obrigatório*, *único*, *string* ] - Data e hora da aceitação do indivíduo para início do atendimento. Lembrando que em caso de não urgência/emergência essa aceitação não é automática;

|||
|:----------------|:---------|
| **Validação**   | Compliance a ISO 8601. |

5. **Modalidade assistencial** [*obrigatório*, *único*, *enum* ] - Tipo de assistência prestada pela unidade de saúde. {*Atenção Básica*, *Ambulatorial Especializada*, *Atenção Domiciliar*, *Atenção Psicossocial*, *Atenção à Urgência/Emergência*}.

6. **Caráter de atendimento** [*obrigatório*, *único*, *enum* ] - Tipo de consulta. {*Consulta agendada*, *Consulta agendada programada: cuidado continuado*, *Demanda espontânea (DE): consulta no dia*, *Demanda espontânea (DE): atendimento de urgência*}.

7. **Profissionais do atendimento** - Profissionais envolvidos no atendimento.

<br>

##### Profissionais do atendimento [*obrigatório*, *único*, *object*]

Os profissionais envolvidos no atendimento são identificados por dois campos principais:

1. **Profissional**;
2. **Identificador do profissional atendente** [*obrigatório*, *único*, *string*, *validação*] - dentificação unívoca do profissional prescritor, mediante número único válido em todo o território nacional, sendo: Cadastro de Pessoa Física (CPF);

|||
|:----------------|:---------|
| **Validação**   | Buscar o CADSUS para conferência. |

###### Profissional [*obrigatório*, *múltiplos*, *object*]

Os dados que idenficam um profissional são:

1. **Nome do profissional** [*opcional*, *único*, *string*].
2. **Número do conselho do profissional atendente** [*obrigatório*, *único*, *string*] - Indica o número do conselho do profissional atendente.
3. **Conselho do profissional atendente** [*obrigatório*, *único*, *enum* ] - Indica a entidade de conselho do profissional atendente (CRM, CRF, CRO,...).
4. **UF do conselho do profissional atendente** [*obrigatório*, *único*, *enum* ] - Indica a UF do Conselho do Profissional atendente.


#### Motivo do Atendimento [*opcional*, *único*, *objeto* ]