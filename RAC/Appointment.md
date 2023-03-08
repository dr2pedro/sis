# Caracterização do Atendimento

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
As propriedades do atendimento contém dados sobre o estabelecimento de saúde e os profissionais que geraram o RAC.

<br>

## Índice

- [Identificador do Estabelecimento de saúde](Appointment.md#identificador-do-estabelecimento-de-saúde)
- [Procedência](Appointment.md#procedência)
- [Identificação da equipe de saúde](Appointment.md#idenficação-da-equipe-de-saúde)
- [Data e hora do atendimento](Appointment.md#data-e-hora-do-atendimento)
- [Modalidade assistencial](Appointment.md#modalidade-assistencial)
- [Caráter de atendimento](Appointment.md#caráter-de-atendimento)
- [Profissionais do atendimento](Appointment.md#profissionais-do-atendimento)
    - [Identificador do profissional atendente](Appointment.md#identificador-do-profissional-atendente)
    - [Profissional](professional.md)

<br>

## Especificação

### Identificador do Estabelecimento de saúde
**conversão**: _Clinical Identification_ ou CID.

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
**conversão**: _Referrer_.

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
**conversão**: _Team Identification_ ou TID.

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
**conversão**: _Date from_ ou _from_.

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
| **Obrigatório**  | Única       |          String        |  true     |

Data e hora da aceitação do indivíduo para início do atendimento. Lembrando que em caso de não urgência/emergência essa aceitação não é automática.

**Validação**
```
1. Dependendo do UseCase, negar lançamentos históricos, ou seja, não permitir lançamentos que sejam anteriores a data do "hoje".
2. Deve seguir a norma ISO 8601.
```

<br>

### Modalidade assistencial
**conversão**: _clinical type_ ou _type_.

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
| **Obrigatório**  | Única       |           Enum         |  false    |

Tipo de assistência prestada pela unidade de saúde.

**Enum**
```
1. Atenção Básica
2. Ambulatorial Especializada  
3. Atenção Domiciliar
4. Atenção Psicossocial
5. Atenção à Urgência/Emergência

---

1. Primary Care
2. Specialized Practice
3. House Care
4. Psychosocial Practice
5. Emergency
```

<br>

### Caráter de atendimento
**conversão**: _Appointment type_ ou _Appointment source_.

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
| **Obrigatório**  | Única       |           Enum         |  false    |

Na verdade essa propriedade lida com a origem da consulta frente à um agendamento ou não agendamento.

**Enum**
```
1. Consulta agendada
2. Consulta agendada programada: cuidado continuado
3. Demanda espontânea (DE): consulta no dia
4. Demanda espontânea (DE): atendimento de urgência

---
1. Booked appointment
2. Booked appointment: continuous care
3. Not booked appointment
4. Urgency
```

<br>

### Profissionais do atendimento
**conversão**: _Professionals_??.

<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
| **Obrigatório**  | Única       |    Objeto     |  false    |

<br>

#### Identificador do profissional atendente
**conversão**: _Main Professional Identification_ ou PID.

<br>

|  Implementação   |  Instância  |     Tipo      | Validação |
|:----------------:|:-----------:|:-------------:|:----------|
| **Obrigatório**  | Única       |    String     |   true    |

Identificação unívoca do profissional prescritor, mediante número único válido em todo o território nacional. Por enquanto esse identificador é o Cadastro de Pessoa Física (CPF).

**Validação**
```
1. Buscar o identificador fornecido no CADSUS.
```

<br>
