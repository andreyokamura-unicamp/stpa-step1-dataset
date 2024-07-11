# STPA - Step 1 - Dataset

## Introdução
Este dataset contém sentenças (registros textuais) gerados e utilizados durante o primeiro passo da técnica de análise de perigo ***System-Theoretic Process Analysis*** (STPA), "Definir o propósito da análise".
Este passo consiste em identificar três aspectos essenciais do sistema, dados por: 
- Perdas ou ***Losses***, são os objetos ou entidades de valor aos stakeholders que não devem sofrer perdas, como vidas humanas, equipamentos ou missão;
- Perigos ao nível de sistema ou ***System-Level Hazards***, são condições do sistema que, em situações de ambiente de pior caso, podem levar às Perdas;
- Restrições ao nível de sistema ou ***System-Level Constraints***, são estados do sistema que devem ser cumpridos para evitar a ocorrência de Perigos.

## Criação do dataset
Este dataset foi criado por meio da extração de sentenças em inglês encontradas em apresentações de STPA realizadas no [*MIT Partnership for Systems Approaches to Safety and Security* (PSASS)](https://psas.scripts.mit.edu/home/), durante o período de 2012-2023.

## Forma de uso
O dataset é um arquivo ".csv".
Para o uso em Python, é recomendado o uso do código seguinte com a bliblioteca Pandas:
```python
import pandas as pd
df = pd.read_csv(r'/[PATH]/stpa-step1-dataset.csv')
```
## Colunas do dataset
Este dataset contém 8 colunas, que organizam as informações coletadas.
1. "sentenca": A sentença extraída;
2. "classe": O rótulo relacionado a sentença;
3. "dominio": O domínio da apresentação;
4. "ano": O ano da apresentação;
5. "titulo": O nome da apresentação;
6. "link": O endereço da apresentação;
7. "slide": O slide em que a sentença foi retirada;
8. "obs": Caso a apresentação não seja explicitamente sobre STPA, descreve o tipo da apresentação.

## Distribuição de dados
As sentenças retiradas são exemplos em tabelas das apresentações do workshop que explicitamente mostram o tipo da sentença (uma tabela com lista de Perdas, uma tabela com lista de Perigos, e uma tabela com lista de Restrições), que automaticamente representam o rótulo correspondente a ser preenchido no dataset.
No entanto, devido a característica da análise e a disponibilidade de exemplos extreaídos, ocorre um desbalanceamento de classes, visto na tabela a seguir.
| Classes  | nº de Sentenças |
| :---     |        ---: |
| loss  | 254  |
| hazard  | 408  |
| constraint  | 316  |
| exloss  | 47  |
| hazard  | 34  |
| constraint  | 19  |
| Total  | 1078  |

O Handbook de STPA (2018) fornece instruções para definição de sentenças de perdas, perigos e restrições do sistema. No entanto, nem todas as sentenças neste dataset segue o formato proposto pelo Handbook. Em vez de excluir estas sentenças não padronizadas, foi optado pela criação das classes "exloss", "exhazard" e "exconstraint", que contém estas sentenças separadas com o objetivo de testar o dataset emexperimentos.

Os critérios para esta separação são os seguintes:

Para Perdas, 1. a sentença deve conter uma palavra chave "loss", "damage", "injury", entre outros, que é ligada à uma perda, ou 2. ser alguma condição do sistema que deve ser evitada.

Para Perigos, 1. a sentença deve mencionar o <sistema>, em conjunto com uma <condição não segura>, ou 2. deve ser algum estado ou condição do sistema, que pode levar à perda.

Para restrições, 1. a sentença deve conter um verbo modal "must", "shall", "should", entre outros, que define uma restrição do sistema, ou 2. deve ser uma forma de minimizar as perdas, caso um perigo ocorra.

## Experimentos de Classificação
Neste repositório foi incluído um notebook em Python para experimentação do dataset. Foram feitos dois experimentos de classificação com os algoritmos de aprendizado de máquina Support vector Machines (SVM) e Naïve Bayes (NB).

Experimento 1: Classificação apenas com as classes "loss", "hazard" e "constraint", para simular casos em que as sentenças de entrada estão em um formato próximo do ideal.

Experimento 2: Classificação das classes "exloss", "exhazard", e "exconstraint", somadas às suas respectivas classes originais, para testar o dataset em um estado sem filtragem (e inclui posíveis sentenças ambíguas ou errôneas).

## Sobre o Autor
Este dataset foi criado pelo mestrando de Sistemas de Informação e Comunicação *Andrey Toshiro Okamura*, da Faculdade de Tecnologia da UNICAMP (Limeira-SP), sob orientação da Profa. Dra. Ana Estela Antunes da Silva.
