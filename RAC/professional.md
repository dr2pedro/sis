# Profissional

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
| **Criado em** | 08-03-2022 |

<br>


## Sobre
Esses são os dados mínimos de identificação de um professional dentro do escopo de um atendimento.

<br>

## Índice

- [Nome do profissional](professional.md#nome-do-profissional)
- [Número do conselho do profissional atendente](professional.md#número-do-conselho-do-profissional-atendente)
- [Conselho do profissional atendente](professional.md#conselho-do-profissional-atendente)
- [UF do conselho do profissional atendente](professional.md#uf-do-conselho-do-profissional-atendente)

<br>

## Especificação

### Nome do Profissional
**conversão**: _Name_.

<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
|     Opcional     | Única       |    String     |  false    |

Nome no formato de String contínua do profissional. Repare que essa não é a identificação.


<br>

### Número do conselho do profissional atendente
**conversão**: _Professional Identification_ ou PID.

<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
| **Obrigatório**  | Única       |    String     |  false    |

Identificador profissional em string.

<br>

### Conselho do profissional atendente
**conversão**: _Council_.

<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
| **Obrigatório**  | Única       |     Enum      |  false    |

Indica a entidade de conselho do profissional.

**Enum**
```
1. CRM
2. COREN
3. CRF
4. CRO
...
```

<br>

### UF do conselho do profissional atendente
**conversão**: _Council Region_.

<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
| **Obrigatório**  | Única       |     Enum      |  false    |

Indica a UF em que essa identificação está registrada.

<br>