# PaPAHR - Pacote da Produtividade Ambulatorial e Hospitalar do R 

<!-- badges: start -->
![CRAN status](https://www.r-pkg.org/badges/version/microdatasus)
<!-- badges: end -->

Este pacote foi desenvolvido para gerar tabelas que alimentam um dashboard de indicadores da Produtividade Ambulatorial e Hospitalar, voltado especificamente para os estabelecimentos de saúde da Rede EBSERH. Ele automatiza a coleta e o tratamento de dados provenientes dos Sistemas de Informação em Saúde do DATASUS, com o objetivo de apoiar a gestão hospitalar na tomada de decisões, promovendo agilidade e padronização na produção de informações estratégicas em saúde.

Atualmente, o pacote integra os seguintes sistemas disponibilizados pelo DATASUS: SIA-PA, SIH-RD, SIH-RJ, SIH-SP e CNES-ST.

Para uma descrição detalhada de cada um desses sistemas, recomenda-se a leitura do e-book elaborado por Raphael Saldanha, disponível neste [link](https://rfsaldanha.github.io/sis/).


# Instalação
Para instalar o pacote **PaPAHR**, é necessário que o pacote `remotes` já esteja instalado no seu ambiente R.

Além disso, o pacote `read.dbc` também deve ser instalado, pois ele é utilizado para a leitura dos arquivos no formato `.dbc`, disponibilizados pelo DataSUS.

Abaixo está o código para instalar o pacote `read.dbc`:

```r
remotes::install_github("danicat/read.dbc")
```
Por fim, utilize o código abaixo para instalar o pacote PaPAHR:
```r
remotes::install_github("abelbrasil/PaPAHR")
```
# Funções
Para utilizar o pacote, o usuário deve selecionar o Sistema de Informação em Saúde (SIS) de interesse — SIA-PA, SIH-RD, SIH-RJ ou SIH-SP. Para cada um desses sistemas, há uma função principal responsável pela criação das tabelas. Além disso, o usuário deve definir a origem dos microdados do DATASUS, que podem ser obtidos diretamente dos servidores do DATASUS ou a partir de um diretório local.

A seguir, são apresentadas as funções principais de cada SIS, organizadas conforme a origem dos dados.
| Funções Principais          | Funções Principais Locais          |
|-----------------------------|------------------------------------|
| ```create_output_PA()```          | ```create_output_PA_from_local()```      |
| ```create_output_SIH_RD()```      | ```create_output_SIH_RD_from_local()```  |
| ```create_output_SIH_RJ()```      | ```create_output_SIH_RJ_from_local()```  |
| ```create_output_SIH_SP()```      | ```create_output_SP_from_local()```      |


Optar por utilizar as funções que acessam diretamente os servidores do DATASUS tem como vantagem não exigir que o usuário baixe previamente os arquivos, automatizando todo o processo de coleta. No entanto, essa opção pode ser mais demorada, pois envolve o download de diversas bases de dados volumosas. Já as funções que utilizam arquivos armazenados localmente são mais rápidas e independem da disponibilidade dos servidores do DATASUS, mas exigem que o usuário já tenha feito o download prévio de todas as bases necessárias para o seu computador.

# Exemplos
A forma de utilização dessas funções é semelhante. A seguir, são apresentados dois exemplos: um para as funções principais e outro para as funções principais locais. 
```r
library(PaPAHR)

dados = create_output_PA(
  year_start = 2023,
  month_start = 1,
  year_end = 2023,
  month_end = 1,
  state_abbr = "CE",
  county_id = NULL,
  health_establishment_id = c("2561492", "2481286"),
  save_csv = TRUE
)

dados = create_output_PA_from_local(
  state_abbr = "CE",
  dbc_dir_path = "X:/USID/BOLSA_EXTENSAO_2024/dbc/dbc-2301-2306",
  county_id = NULL,
  health_establishment_id = c("2561492", "2481286"),
  save_csv = TRUE
)
```

# Informações de contato
Caso tenha alguma dúvida, entre em contato comigo pelo e [gustaa1320\@gmail.com](mailto:gusta1320@gmail.com).
