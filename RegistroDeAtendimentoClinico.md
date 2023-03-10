# Registro de Atendimento Clínico 
**Fonte**: [PORTARIA Nº 234, DE 18 DE JULHO DE 2022](https://www.in.gov.br/en/web/dou/-/portaria-n-234-de-18-de-julho-de-2022-416506215)

<br>

|||
|:-------------:|:------------|
|  **Autores**  | [Pedro Paulo dos Santos](https://github.com/dr2pedro), [Felipe Lima](), [José Antonio Hojota]() e Lorena Martins |
| **Criado em** | 05-03-2022 |

<br>

## Índice

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
        - [Motivo do Atendimento Estruturado](RegistroDeAtendimentoClinico.md#motivo-do-atendimento-estruturado-opcional-múltiplo-array)
    - [Observações](RegistroDeAtendimentoClinico.md#observações-opcional-único-objeto)
        - [Sinais Vitais](RegistroDeAtendimentoClinico.md#sinais-vitais-opcional-único-objeto)
            - [Pressão Arterial](RegistroDeAtendimentoClinico.md#pressão-arterial-opcional-único-objeto)
        - [Medições](RegistroDeAtendimentoClinico.md#registro-de-atendimento-clínico)
            - [Peso](RegistroDeAtendimentoClinico.md#peso-opcional-único-number)
            - [Altura](RegistroDeAtendimentoClinico.md#altura-opcional-único-number)
            - [Perímetro Cefálico](RegistroDeAtendimentoClinico.md#perímetro-cefálico-opcional-único-number)
            - [Circunferência Abdominal](RegistroDeAtendimentoClinico.md#circunferência-abdominal-opcional-único-number)
        - [Informações Adicionais](RegistroDeAtendimentoClinico.md#informações-adicionais-opcional-único-objeto)

    
<br>

## Resumo

<br>

## Motivação

Os sistemas de informação em saúde (SIS) disponíveis no mercado atualmente abordam o cuidado em saúde como um sistema de histórico de cuidado, excluindo a perspectiva centrada no paciente, desconsiderando sua segurança e seus direitos, sem qualquer cuidado com os dados produzido no atendimento e impedindo a interoperabilidade com outros atores do sistema.

Os profissionais que utilizam esses sistemas na maioria das vezes são obrigados a registrarem diversas entradas manualmente, duplicado informações já registradas por colegas que atenderam o paciente anteriormente.

Os gestores de estabelecimentos de saúde dependem de mapeamentos personalizados para emitir relatórios compilados dos cuidados prestados pela sua unidade.

Com a implementação do padrão, previsto em lei, do Registro de Atendimento Clínico (RAC) será possível gerenciar o cuidado focado no paciente, permitir que o profissional de saúde tenha acesso a informações previamente fornecidas pelo paciente aos profissionais anteriores, reduzir a inserção manual de dados não padronizados e permitir que os registros sejam compilados de forma a facilitar a emissão de relatórios.

<br>

---

## StakeHolders

Os atores mencionados na lei como partes interessadas na implementação do Registro de Atendimento Clínico são:

1. Profissionais de saúde de atendimentos ambulatóriais e aqueles venham a atender o paciente em regime de urgência/emergência;

2. Estabelecimentos de saúde;

3. HealthTechs;

4. Gestores e especialistas clínicos (_escopo aberto_), _i.e._ coordenadores regionais de saúde da mulher ou saúde da criança;

5. Entidades representativas dos usuários do serviço de saúde, _i.e._ comissão de saúde;

6. Especialistas de linhas de cuidado do indivíduo (_escopo fechado_), _i.e._ o reumatologista da paciente;

7. O próprio paciente e/ou seus responsáveis (_escopo aberto_);

<br>

---

## Especificação

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

---

### Observações [*opcional*, *único*, *objeto*]
A propriedade observações é uma propriedade opcional, de objetos opcionais mas que, caso existam, possuem propriedade obrigatórias. A maioria das observações são objetos de valor.

1. **Sinais Vitais**;
2. **Medições**;
3. **Informações adicionais**;

<br>

#### Sinais Vitais [*opcional*, *único*, *objeto*]
Na verdade o único sinal vital descrito na normativa, que ainda é opcional, é o registro da **Pressão Arterial**.

<br>

##### Pressão Arterial [*opcional*, *único*, *objeto*]

1. **Sistólica** [*obrigatório*, *único*, *number*];
2. **Unidade de medida da Pressão arterial Sistólica** [*obrigatório*, *único*, *enum*] - {*mmHg*};
3. **Diastólica** [*obrigatório*, *único*, *number*];
4. **Unidade de medida da Pressão arterial Diastólica** [*obrigatório*, *único*, *enum*] - {*mmHg*};
5. **Posição do indivíduo na aferição** [*opcional*, *único*, *enum*] - Indica a posição do indivíduo no momento da aferição da pressão arterial. {*Em pé*, *Sentado*, *Reclinado*, *Deitado*, *Deitado com inclinação para esquerda*};
6. **Local de aferição** [*opcional*, *único*, *enum*] - Identifica qual parte do corpo humano foi utilizada para aferir a pressão arterial. {*Braço direito*, *Braço esquerdo*, *Coxa direita*, *Coxa esquerda*, *Pulso direito*, *Pulso esquerdo*, *	
Tornozelo direito*, *Tornozelo esquerdo*, *Dedo da mão*, *Dedo do pé*}.

<br>

#### Medições [*opcional*, *único*, *objeto*]
As medições consistem em: Peso, Altura, Perímetro Encefálico e Circunferência Abdominal. Repara que nem todas serão utilizadas ao mesmo a depender da linha de cuidado.

<br>

##### **Peso** [*opcional*, *único*, *number*]
1. **Unidade de medida do peso** [*obrigatório*, *único*, *enum*] - Segue os padrões [HL7-FIHR](http://hl7.org/fhir/R4B/valueset-ucum-bodyweight.html) para identificar a unidade de medida. {*kg*, *lb_av*, *g*}.
2. **Posição em relação à gravidade** [*opcional*, *único*, *enum*] - Segue o padrão [LOINC](https://loinc.org/8361-8/ehttps:/loinc.org/8352-7/) para determinar a posição que a mensuração foi realizada. {*de pé*, *deitado*, *sentado*}.
3. **Roupas usadas durante a medição** [*opcional*, *único*, *enum*] - Segue o padrão [LOINC](https://loinc.org/8352-7/) para determinar a vestimenta no momento da mensuração. {*Roupa íntima ou menos*, *Roupas de rua, sem sapatos*, *Roupas e sapatos de rua*};
4. **Origem da medição** [*obrigatório*, *único*, *enum*] - Informar se o peso foi aferido no atendimento ou relatado. {*Medido*, (3141-9); *Relatado* (3142-7)}.

<br>

##### **Altura** [*opcional*, *único*, *number*]
1. **Unidade de medida da altura** [*obrigatório*, *único*, *enum*] - Segue os padrões [HL7-FIHR](http://hl7.org/fhir/ValueSet/ucum-bodylength) para identificar a unidade de medida. {*cm*, *in_i*}.
2. **Posição em relação à gravidade** [*opcional*, *único* *enum*] - Segue o padrão [LOINC](https://loinc.org/8361-8/ehttps:/loinc.org/8352-7/) para determinar a posição que a mensuração foi realizada. {*de pé*, *deitado*, *sentado*}.
3. **Origem da medição** [*obrigatório*, *único*, *enum*] - Informar se o peso foi aferido no atendimento ou relatado. {*Medido*, (3141-9); *Relatado* (3142-7)}.

<br>

##### **Perímetro cefálico** [*opcional*, *único*, *number*]
1. **Unidade de medida do perímetro cefálico** [*obrigatório*, *único*, *enum*] - Segue os padrões [HL7-FIHR](http://hl7.org/fhir/ValueSet/ucum-bodylength) para identificar a unidade de medida. {*cm*, *in_i*}.

<br>

##### **Circunferência abdominal** [*opcional*, *único*, *number*];
1. **Unidade de medida da Circunferência Abdominal** [*obrigatório*, *único*, *enum*] - Segue o padrão [LOINC](https://loinc.org/8361-8/ehttps:/loinc.org/8352-7/) para determinar a unidade de medida da circunferência abdominal. {*cm*, *in_us*}.

<br>


#### Informações adicionais [*opcional*, *único*, *objeto*]
As informações adicionais são classificações que não são Medições, Sinais Vitais e nem propriedades da doença/problema principal do atendimento.

1. **DUM (Data da Última Menstruação)** [*opcional*, *único*, *date*, *validação*] - 

|||
|:----------------|:---------|
| **Validação**   | ISO 8601. |

2. **Idade gestacional** [*opcional*, *único*, *number*] - Quantidade indicada em dias ou semanas.
2.1. **Unidade de medida da Idade Gestacional** [*obrigatório*, *único*, *enum*] - {*dias*, *semanas*};

3. **Quantidade de gestas prévias** [*opcional*, *único*, *number*];
4. **Quantidade de Partos** [*opcional*, *único*, *number*];
5. **Quantidade de Abortos** [*opcional*, *único*, *number*];
6. **Tipo de aleitamento materno para crianças até 2 anos** [*opcional*, *único*, *enum*] - {*Predominante*, *Complementado*, *Inexistente*};

<br>

### Problemas / diagnósticos avaliados