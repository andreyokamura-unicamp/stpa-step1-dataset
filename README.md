# STPA - Step 1 - Dataset

## Introdução
Este dataset contém sentenças (registros textuais) gerados e utilizados durante o primeiro passo da técnica de análise de perigo ***System-Theoretic Process Analysis*** (STPA), "Definir o propósito da análise".
Este passo consiste em identificar três aspectos essenciais do sistema, dados por: 
- Perdas ou ***Losses***, são os objetos ou entidades de valor aos stakeholders que não devem sofrer perdas, como vidas humanas, equipamentos ou missão;
- Perigos ao nível de sistema ou ***System-Level Hazards***, são condições do sistema que, em situações de ambiente de pior caso, podem levar às Perdas;
- Restrições ao nível de sistema ou ***System-Level Constraints***, são estados do sistema que devem ser cumpridos para evitar a ocorrência de Perigos.

## Criação do dataset
Este dataset foi criado por meio da extração de sentenças em inglês encontradas em apresentações de STPA realizadas no [*MIT Partnership for Systems Approaches to Safety and Security* (PSASS)](https://psas.scripts.mit.edu/home/), durante o período de 2012-2022.
Também estão inclusas sentenças extraídas de trabalhos sobre STPA, de uma disciplina de Sistemas Críticos lecionada pelo Prof. Dr. Luiz Eduardo Galvão Martins, da Universidade Federal de São Paulo (UNIFESP). Estes exemplos foram traduzidos para a lingua inglesa.

## Forma de uso
O dataset é um arquivo ".csv", com separação por TAB, pois existem vígulas dentro de sentenças e podem impactar na organização do documento.
Para o uso em Python, é recomendado o uso do código seguinte com a bliblioteca Pandas:
```python
import pandas as pd
df = pd.read_csv('/[PATH]/stpa-step1-dataset.csv', sep='\t', names=['req','label'])
}
```
O uso do atributo "*names=*" para definição de nome de colunas é opcional.

## Distribuição de dados
As sentenças retiradas são exemplos em tabelas das apresentações do workshop que explicitamente mostram o tipo da sentença (uma tabela com lista de Perdas, uma tabela com lista de Perigos, e uma tabela com lista de Restrições), que automaticamente representam o rótulo correspondente a ser preenchido no dataset.
No entanto, devido a característica da análise e a disponibilidade de exemplos extreaídos, ocorre um desbalanceamento de classes, visto na tabela a seguir.
| Classes  | nº de Sentenças |
| :---     |        ---: |
| LOSSES  | 304  |
| HAZARDS  | 5544  |
| CONSTRAINTS  | 424  |
| Total  | 1272  |

## Sobre o Autor
Este dataset foi criado pelo mestrando de Sistemas de Informação e Comunicação *Andrey Toshiro Okamura*, da Faculdade de Tecnologia da UNICAMP (Limeira-SP), sob orientação da Profa. Dra. Ana Estela Antunes da Silva.
