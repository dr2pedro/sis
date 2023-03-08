# Motivo do Atendimento

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|     Opcional     | Única       |          Objeto        |   false   |

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
| **Criado em** | 08-03-2022 |

<br>


## Sobre
O que levou o paciente a buscar a unidade de saúde para àquele atendimento clínico.

<br>

## Índice

- [Motivo do atendimento estruturado](Motive.md#motivo-do-atendimento-estruturado)
    - [Terminologia que descreve o motivo do atendimento](Motive.md#terminologia-que-descreve-o-motivo-do-atendimento)
    - [Código do motivo do atendimento](Motive.md#código-do-motivo-do-atendimento)
- [Declaração subjetiva do indivíduo para o atendimento](Motive.md#declaração-subjetiva-do-indivíduo-para-o-atendimento)

<br>

## Especificação

### Motivo do atendimento estruturado
**conversão**: _Reason_??.

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|      Opcional    | Múltiplo    |    Lista de Objetos    |   false   |

Esse motivo na realidade é o que seria conhecido como "código da doenças/problema", onde antes se inseria o CID apenas, agora é possível inserir o código e identificar o classificador para permitir trabalhar com cid-9, cid-10, cid-11, ciap-1 e ciap-2.

<br>

#### Terminologia que descreve o motivo do atendimento
**conversão**: _Classifier_.

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
| **Obrigatório**  | Único       |           Enum         |   false   |

Identificação do classificador.

**Enum**
```
1. CID
2. CIAP
```

<br>

#### Código do motivo do atendimento
**conversão**: _Code_.

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|     Opcional     | Único       |           Enum         |   false   |

O código do CID ou do CIAP.

**Enum**
```
Pegar os códigos de cada classificador incluinso suas versões.
```

<br>

### Declaração subjetiva do indivíduo para o atendimento
**conversão**: _Notes_.

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|      Opcional    | Único       |         String         |   false   |

Campo de livre para anotações referentes sobre o motivo do atendimento.

<br>

