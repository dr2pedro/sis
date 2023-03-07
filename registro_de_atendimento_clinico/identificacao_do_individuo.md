# Identificação do Indivíduo

## Licença

CC0 1.0 Universal

    CREATIVE COMMONS CORPORATION IS NOT A LAW FIRM AND DOES NOT PROVIDE
    LEGAL SERVICES. DISTRIBUTION OF THIS DOCUMENT DOES NOT CREATE AN
    ATTORNEY-CLIENT RELATIONSHIP. CREATIVE COMMONS PROVIDES THIS
    INFORMATION ON AN "AS-IS" BASIS. CREATIVE COMMONS MAKES NO WARRANTIES
    REGARDING THE USE OF THIS DOCUMENT OR THE INFORMATION OR WORKS
    PROVIDED HEREUNDER, AND DISCLAIMS LIABILITY FOR DAMAGES RESULTING FROM
    THE USE OF THIS DOCUMENT OR THE INFORMATION OR WORKS PROVIDED
    HEREUNDER.

<br>

|||
|:-------------:|:------------|
|  **Autor(es)**  | [Pedro Paulo dos Santos](https://github.com/dr2pedro)
| **Criado em** | 05-03-2022 |

<br>


## Sobre
Para a identificação do indivíduo utiliza-se o Cadastro Nacional Pessoa Física (CPF) ou a Carteira Nacional de Saúde (CNS). Caso nenhum o paciente não possua nenhum dos dois documentos no momento o Registro de Atendimento Clínica utilizam-se então variáveis demográficas que serão descritas a seguir.

<br>

## Índice

- [Identificador Nacional](identificacao_do_individuo.md#identificador-nacional)
- [Identificadores Demográficos](identificacao_do_individuo.md#identificadores-demográficos)
    - [Nome Completo](identificacao_do_individuo.md#nome-completo)
    - [Nome Social](identificacao_do_individuo.md#nome-social)
    - [Nome completo da Mãe](identificacao_do_individuo.md#nome-completo-da-mãe)
    - [Data de Nascimento](identificacao_do_individuo.md#data-de-nascimento)
    - [Sexo](identificacao_do_individuo.md#sexo)
    - [País de Nascimento](identificacao_do_individuo.md#país-de-nascimento)
    - [Município de Nascimento](identificacao_do_individuo.md#município-de-nascimento)
- [Endereço](identificacao_do_individuo.md#endereço)

<br>

## Especificação

### Identificador Nacional 

<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
|  **Obrigatório** | Única       |    String     |  true     |

A sequência numérica que do CPF (11 digitos) ou da CNS (15 digitos).

**Validação**

```
1. Conferir se os dígitos são válidos;
2. Em caso de CPF, consultar se existe a CNS, caso não deve ser criada e adicionada;
```

<br>

### Identificadores Demográficos

<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
|    Opcional      | Única       |    Objeto     |  true     |


Os idenficadores demográficos só devem ser usadas caso o paciente não possua CPF e CNS no momento do RAC. Repare que os que representam algum tipo de referência geográfica não são obrigatórios uma vez que a identificação do indivíduo já contém o endereço.

**Validação**

```
1. Obrigatório na ausência do Identificador Nacional;
```

<br>

#### Nome Completo
#### Nome Social
#### Nome completo da Mãe
#### Data de Nascimento
#### Sexo
#### País de Nascimento
#### Município de Nascimento

<br>

## Endereço