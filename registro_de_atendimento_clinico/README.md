# Registro de Atendimento Clínico 
**Fonte**: [PORTARIA Nº 234, DE 18 DE JULHO DE 2022](https://www.in.gov.br/en/web/dou/-/portaria-n-234-de-18-de-julho-de-2022-416506215)

<br>

|||
|:-------------:|:------------|
|  **Autores**  | [Pedro Paulo dos Santos](https://github.com/dr2pedro), [Felipe Lima](), [José Antonio Hojota]() e Lorena Martins |
| **Criado em** | 05-03-2022 |

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

## Especificação/Índice

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

**Vale lembrar que esta lei não opina  sobre o prontuário, apenas o RAC.**

<br>