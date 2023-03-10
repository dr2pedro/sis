# Identificação do Indivíduo

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|  **Obrigatório** | Única       |          Objeto        |   false   |

<br>

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

- [Identificador Nacional](Id.md#identificador-nacional)
- [Identificadores Demográficos](Id.md#identificadores-demográficos)
    - [Nome Completo](Id.md#nome-completo)
    - [Nome Social](Id.md#nome-social)
    - [Nome completo da Mãe](Id.md#nome-completo-da-mãe)
    - [Data de Nascimento](Id.md#data-de-nascimento)
    - [Sexo](Id.md#sexo)
    - [País de Nascimento](Id.md#país-de-nascimento)
    - [Município de Nascimento](Id.md#município-de-nascimento)
- [Endereço](Id.md#endereço)

<br>

## Especificação

### Identificador Nacional 
**conversão**: _Identification_ ou ID.

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
**conversão**: _Social Identification_ ou SID.
<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
|      Opcional    | Única       |    Objeto     |  true     |


Os idenficadores demográficos só devem ser usadas caso o paciente não possua CPF e CNS no momento do RAC. Repare que os que representam algum tipo de referência geográfica não são obrigatórios uma vez que a identificação do indivíduo já contém o endereço.

**Validação**

```
1. Obrigatório na ausência do Identificador Nacional;
```

<br>

#### Nome completo
**conversão**: _Full name_.
<br>

|  Implementação   |  Instância  |         Tipo           | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
| **Obrigatório**  | Única       |    Lista de String     |  false    |

Nome completo sem abreviações, implementado em lista com ordem específica. Repare que o separador pode não ser o espaço visto que determinadas pessoas possem nomes compostos, i.e., Pedro Paulo, João Lucas, etc.

<br>

#### Nome social
**conversão**: _Social name_.

<br>

|  Implementação   |  Instância  |         Tipo           | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|     Opcional     | Única       |    Lista de String     |  false    |

Esse é o nome que a pessoa gostaria de ser identificada, sendo opcional nos casos de identificação apenas pelo nome completo ou suas partes. Repare que aqui não é apenas para pessoas que se identificam por outro genêro, mas também por pessoas com nomes adquiridos, apelidos e etc.

<br>

#### Nome completo da mãe
**conversão**: _Mother's name_.
<br>

|    Implementação    |  Instância  |         Tipo           | Validação |
|:-------------------:|:-----------:|:----------------------:|:----------|
|   **Obrigatório**   | Única       |    Lista de String     |  false    |

Esse campo possui a mesma função do campo filiação das cédulas de identidade nacional.

<br>

#### Data de Nascimento
**conversão**: _Birthdate_.
<br>

|    Implementação    |  Instância  |         Tipo           | Validação |
|:-------------------:|:-----------:|:----------------------:|:----------|
|   **Obrigatório**   | Única       |        String          |   true    |

Repare que o campo necessita de uma string e não um tipo Date, que irá aparecer mais tarde em outro objeto de construção do RAC.

**Validação**
```
1. Deve seguir a norma ISO 8601.
```

<br>

#### Sexo
**conversão**: _Gender_.
<br>

|    Implementação    |  Instância  |         Tipo           | Validação |
|:-------------------:|:-----------:|:----------------------:|:----------|
|   **Obrigatório**   | Única       |         Enum           |   false   |

Identificação do sexo da pessoa, não se refere a orientação sexual, identidade de gêneros e afins.

**Enum**
```
1. Masculino
2. Feminino

---

1. Male
2. Female
```

<br>

#### País de Nascimento
**conversão**: _Country_.
<br>

|    Implementação    |  Instância  |         Tipo           | Validação |
|:-------------------:|:-----------:|:----------------------:|:----------|
|       Opcional      | Única       |          Enum          |   false   |

Como mecionado anteriormente, esse campo não é obrigatório visto que irá replicar uma informação que estará contido no campo endereço.

**Enum**
```
Buscar na API do IBGE a identificação numérica oficial dos países.
```

<br>

#### Município de Nascimento
**conversão**: _City_.
<br>

|    Implementação    |  Instância  |         Tipo           | Validação |
|:-------------------:|:-----------:|:----------------------:|:----------|
|       Opcional      | Única       |          Enum          |   false   |

O mesmo mencionado para o país de nascimento.

**Enum**
```
Buscar na API do IBGE a identificação numérica oficial dos municípios.
```

<br>

### Endereço
**conversão**: _Address_.
<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|  **Obrigatório** | Única       |    Lista de String     |  true     |

Uma sequencia contendo os nomes do logradouro em ordem de precedência.

**Validação**
```
1. Só registrado caso a primeira ocorrência da lista seja Brasil, caso contrário, descartado.
```

<br>

**Dica**
```
Em um sistema geolocalizado a referência dessas strings define objetos geojson agregados em si. Consultar [tesa - tools for easy spatial analysis](https://github.com/CodePlayData/tesa).
```
