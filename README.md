# Repositório de dados municipais [![Build Status](https://travis-ci.org/simkimsia/UtilityBehaviors.png)](https://travis-ci.org/simkimsia/UtilityBehaviors)

>> [em construção] Neste repositório são reunidos dados dos municípios brasileiros presentes em:

    * Bases

    * Pacotes do R

    * Indicadores

## Bases

[Códigos dos Mun.(IBGE, TSE, Receita, etc)](http://basedosdados.org/dataset/diretorio-municipios-brasileiros/resource/c1deb363-ffba-4b1e-95dc-c5e08311852e)

Munics IBGE - ftp://ftp.ibge.gov.br/Perfil_Municipios

Pib dos Municípios - ftp://ftp.ibge.gov.br/Pib_Municipios; [ver também](https://www.ibge.gov.br/apps/pibmunic/) 

[https://cidades.ibge.gov.br/](https://cidades.ibge.gov.br/)

Censo Suas

DataSus

[dadosabertos - Municípios do Brasil](https://dadosabertos.social/t/municipios-do-brasil/331)

[Munics-IPs](https://github.com/ronycoelho/Bases-Munics-IPs-e-Estadics-IPs)

[Replication data for: Looking to the Next Election: Electoral Incentives as a Force Against Corruption in Brazilian Municipalities](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/Q4KZFQ)

[IPEADATA - Nível: municípios](http://www.ipeadata.gov.br/Default.aspx)

[Municipios Brasileiros - lat e long](https://github.com/kelvins/Municipios-Brasileiros)

[Base dos dados, "municípios"](https://basedosdados.org/dataset/?q=munic%C3%ADpios)

[Panaroma do Legislativo Municipal](https://www.senado.leg.br/institucional/datasenado/panorama/#/)

[Índice de Concorrência dos Municípios](https://produto.patri.com.br/others/disparo/preview/138425/5/YWxs)

[Censo Legislativo](https://basedosdados.org/dataset/censo-legislativo)

[REGIC - Regiões de Influência das Cidades](https://www.ibge.gov.br/geociencias/cartas-e-mapas/redes-geograficas/15798-regioes-de-influencia-das-cidades.html?=&t=o-que-e)

[API de localidades](https://servicodados.ibge.gov.br/api/docs/localidades#api-_)

[Localidades | 2010 - IBGE](https://www.ibge.gov.br/geociencias/organizacao-do-territorio/estrutura-territorial/27385-localidades.html?edicao=27386&t=o-que-e)

## Pacotes

[ribge](https://github.com/tbrugz/ribge)

tsemun <- tse_municipios()

[brcities](https://github.com/abjur/brcities)

[electionsBr](http://electionsbr.com/)

[geobr](https://cran.r-project.org/web/packages/geobr/vignettes/intro_to_geobr.html)

[owdbr - Open Welfare Data Brazil](https://cran.r-project.org/web/packages/owdbr/owdbr.pdf)

[munifacil](https://github.com/curso-r/munifacil)


## Indicadores
[Índice de Desenvolvimento Sustentável das Cidades](https://idsc-br.sdgindex.org/)

[IVS - Atlas da Vulnerabilidade Social nos Municípios](http://ivs.ipea.gov.br/index.php/pt/planilha) 

[Ranking Nacional da Transparência](http://combateacorrupcao.mpf.mp.br/ranking)

[Indíce de desenvolvimento municipal Firjan](https://www.firjan.com.br/ifdm/)

[Indíce Firjan de gestão municipal](https://www.firjan.com.br/ifgf/downloads/download-ifgf-indice-firjan-de-gestao-fiscal.htm) [See also](https://www.bbc.com/portuguese/brasil-54669538?at_custom1=%5Bpost+type%5D&at_campaign=64&at_custom3=BBC+Brasil&at_medium=custom7&at_custom2=facebook_page&at_custom4=E75DF42A-228C-11EB-B49F-116F96E8478F&fbclid=IwAR3LtC9aGRIAzveqiCMO9A-huVc6GgMwrrsBQa-GCLd4GNckQBps8mwGsMQ)

[Mapa Brasil Transparente](https://mbt.cgu.gov.br/publico/home)

[Escala Brasil Transparente](https://relatorios.cgu.gov.br/Visualizador.aspx?id_relatorio=23)

[Índice de desenvolvimento municipal sustentável - CNM](https://www.cnm.org.br/municipios/idms). (Acesso não público)

## Outros

[zonas eleitorais](https://github.com/mapaslivres/zonas-eleitorais)

[Códigos dos Municípios IBGE](https://www.ibge.gov.br/explica/codigos-dos-municipios.php?fbclid=IwAR0fQq6r3RxHH88QFgJhkR6hCAc7TAx-a5RCL1xi703swS1M-hldaxJhyVc)

[Raio-X dos Municípios (2020)](https://raioxdosmunicipios.insper.edu.br/)

[Siconfi](https://siconfi.tesouro.gov.br/siconfi/index.jsf)

[Meu município](https://meumunicipio.org.br/)

[Compara Brasil](http://comparabrasil.com/)


Instituto Brasileiro de Administração Municipal – IBAM - http://www.ibam.org.br/home

Nepol - Núcleo de pesquisa sobre política local https://nepolufjf.wordpress.com/bases-de-dados/

https://painelgfs.tesouro.gov.br/

https://rpubs.com/jadsonbitencourt

[kelvins/Municipios-Brasileiros](https://github.com/kelvins/Municipios-Brasileiros/blob/main/csv/municipios.csv)

## -
Cluster: população, região, estado, idade, hierarquia, pib per capta, idh(?); gini; gestões partidárias(?)


## - 
[Participation, partnerships and planning](https://ronycoelho.github.io/ippc/capacities_englishversion.html)


```
#Sedes
geo_info_seat <- geobr::read_municipal_seat() %>% 
  rename(codigo_ibge = code_muni ) %>% 
    as_tibble() %>% 
    separate(geom,  sep = " ", into = c("lat", "long")) %>% 
    mutate(lat = str_remove(str_remove(lat, "(c\\()"), ","),
           long = str_remove(long, "\\)"))%>%
   mutate(lat = as.double(lat), long = as.double(long)) %>% 
  select(codigo_ibge, lat, long)
  
 # Centroids
geo_info <- geobr::read_municipality() %>% rename(codigo_ibge = code_muni )

# Excuir, pois erro no calculo
geo_info <- geo_info %>% 
  slice(-c(67, 2260))

geo_info$centroid <- sf::st_centroid(geo_info$geom)

geo_info <- geo_info %>% 
  separate(centroid,  sep = " ", into = c("lat", "long")) %>% 
    mutate(lat = str_remove(str_remove(lat, "(c\\()"), ","),
           long = str_remove(long, "\\)")) %>% 
    mutate(lat = as.double(lat), long = as.double(long))
```

### muni_codes
```{r}
code_muni <- 
  function(){
  library(dplyr)
  geobr::read_municipal_seat() %>% 
  as_tibble() %>% 
  dplyr::select(code_muni, name_muni, abbrev_state, name_region)  
  }  

muni <- code_muni()  
```
