# Caracterização do Atendimento

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
As propriedades do atendimento contém dados sobre o estabelecimento de saúde e os profissionais que geraram o RAC.

<br>

## Índice

- [Identificador do Estabelecimento de saúde](appointment.md#identificador-do-estabelecimento-de-saúde)
- [Procedência](appointment.md#procedência)
- [Identificação da equipe de saúde](appointment.md#idenficação-da-equipe-de-saúde)
- [Data e hora do atendimento]()
- [Modalidade assistencial]()
- [Caráter de atendimento]()
- [Profissionais do atendimento]()
    - [Identificador do profissional atendente]()
    - [Profissional]()
        - [Nome do profissional]()
        - [Número do conselho do profissional atendente]()
        - [Conselho do profissional atendente]()
        - [UF do conselho do profissional atendente]()

<br>

## Especificação

### Identificador do Estabelecimento de saúde

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|  **Obrigatório** | Única       |          String        |   true    |

Os digítos do Cadastro Nacional de Estabelecimento de Saúde que é obrigatório em todo território nacional.

**Validação**
```
1. Permitir apenas 8 dígitos.
```

<br>

### Procedência

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|  **Obrigatório** | Única       |          Enum          |  false    |

Identifica o serviço que encaminhou o indivíduo ou a sua iniciativa/de seu responsável na busca pelo acesso ao serviço de saúde.

**Enum**
```
1. Ordem Judicial
2. Retorno
3. Demanda espontânea
4. Demanda referenciada
```

<br>

### Idenficação da equipe de saúde

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|     Opcional     | Única       |          String        |  true     |

Número válido do Identificador Nacional de Equipe (INE) para casos de atendimento em saúde pública, ignorado caso particular.

**Validação**
```
1. Verificar se a quantidade de dígitos é válida (são 7 digítos se não me engano).
2. Ignorado caso CNES particular.
```

<br>

### Data e hora do atendimento

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
| **Obrigatório**  | Única       |          String        |  true     |

