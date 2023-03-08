# Observações

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
Esse objeto contém todas as informações de saúde que são auxiliares a identificação dos problemas relatados, _i.e._ as medições, sinais vitais, informações de linhas de cuidados específicas.

<br>

## Índice

- [Sinais vitais](notes.md#sinais-vitais)
    - [Pressão arterial]()
        - [Sistólica]()
        - [Unidade de medida da Pressão arterial Sistólica]()
        - [Diastólica]()
        - [Unidade de medida da Pressão arterial Diastólica]()
        - [Posição do indivíduo na aferição]()
        - [Local de aferição]()
- [Medições]()
    - [Peso]()
    - [Altura]()
    - [Perímetro cefálico]()
    - [Circunferência abdominal]()
- [Informações adicionais]()
    - [DUM (Data da Última Menstruação)]()
    - [Idade gestacional]()
        - [Unidade de medida da Idade Gestacional]()
    - [Quantidade de gestas prévias]()
    - [Quantidade de Partos]()
    - [Quantidade de Abortos]()
    - [Tipo de aleitamento materno para crianças até 2 anos]()
    - [Exposição à substâncias](substance.md)

<br>

## Especificação

### Sinais vitais
**conversão**: _Vital measure_.

<br>

|  Implementação   |  Instância  |        Tipo        | Validação |
|:----------------:|:-----------:|:------------------:|:----------|
|     Opcional     | Único       |        Objeto      |  false    |

O único sinal vital presente na implementação por enquanto é a aferição de pressão arterial. Aqui, existe possibilidade para expansão como, _i.e._ batimentos cardíacos, frequência respiratória e afins.

<br>

#### Pressão arterial
**conversão**: _Blood pressure_.

<br>

|  Implementação   |  Instância  |        Tipo        | Validação |
|:----------------:|:-----------:|:------------------:|:----------|
|     Opcional     | Único       |        Objeto      |  false    |

