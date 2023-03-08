# Exposição à substâncias

<br>

|  Implementação   |  Instância  |           Tipo         | Validação |
|:----------------:|:-----------:|:----------------------:|:----------|
|     Opcional     | Múltiplo    |   Lista de Objetos     |   false   |

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

<br>

## Índice

- [Uso de álcool, tabaco e outras substâncias nos últimos 3 meses](Substance.md#uso-de-álcool-tabaco-e-outras-substâncias-nos-últimos-3-meses)
    - [Substância](Substance.md#substância)
    - [Outras substâncias não especificadas](Substance.md#outras-substâncias-não-especificadas)
    - [Frequência nos últimos 3 meses](Substance.md#frequência-nos-últimos-3-meses)

<br>

## Especificação

### Uso de álcool, tabaco e outras substâncias nos últimos 3 meses
**conversão**: _Recent substance abuse_.

<br>

|  Implementação   |  Instância  |        Tipo        | Validação |
|:----------------:|:-----------:|:------------------:|:----------|
|     Opcional     | Múltiplo    |  Lista de Objetos  |  false    |

Um agregado de substâncias que foram usadas em um passado recente, 3 meses. Aqui entram drogas ilícitas e lícitas.

<br>

#### Substância
**conversão**: _Substance_.

<br>

|  Implementação   |  Instância  |        Tipo        | Validação |
|:----------------:|:-----------:|:------------------:|:----------|
|     Opcional     | Único       |        Enum        |  false    |

Um identificador indicando se é álcool ou tabaco, caso sejam outras substâncias devem ser registrados no campo seguinte.

**Enum**
```
1. Derivados do tabaco
2. Bebidas alcoólicas

---

1. Tobacco derivatives
2. Alcohol

```

<br>

#### Outras substâncias não especificadas
**conversão**: _Others substances_.

<br>

|  Implementação   |  Instância  |        Tipo        | Validação |
|:----------------:|:-----------:|:------------------:|:----------|
|     Opcional     | Único       |        String      |  true     |

Caso não seja álcool e tabaco, local para identificar a substância abusada.

**Validação**
```
1. Apenas aceitar o campo caso a substância não seja álcool ou tabaco.
```

<br>

#### Frequência nos últimos 3 meses
**conversão**: _3 month frequency_.

<br>

|  Implementação   |  Instância  |        Tipo        | Validação |
|:----------------:|:-----------:|:------------------:|:----------|
|     Opcional     | Único       |         Enum       |  false    |

A frequência de uso dos últimos 3 meses classifica em categorias.

**Enum**
```
1. Nunca
2. Mensalmente
3. 2 ou mais vezes ao mês
4. Semanalmente
5. Diariamente ou quase todos os dias

---

1. Never
2. Monthly
3. Twice or more per month
4. Weekly
5. Daily ou almost
```