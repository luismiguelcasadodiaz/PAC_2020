# PAC_2020
Jupyter notebook to show me which companies by province got bigger subsidies from European Agricultural Guarantee Fund. That hinted my commercial actions


[Data sourced from[(https://www.fega.gob.es/es/datos-abiertos/consulta-de-beneficiarios-pac/descarga-de-ficheros)
1964511 lines of text are fed into a pandas dataframe

```python

Source_data = "Beneficiarios_municipio_ejercicio_2020.txt"
cabeceras = ["BENEFICIARIO","PROVINCIA","MUNICIPIO","MEDIDA","IMPORTE_EUROS","Vacio"]
dtipo_campos={
    'BENEFICIARIO': str,
    'PROVINCIA': str,
    'MUNICIPI': str,
    'MEDIDA': str,
    'IMPORTE_EUROS':str,
    'vacio':str}
separador=';'
PAC_2021_df = pd.read_csv(Source_data,names=cabeceras,sep=separador,error_bad_lines=True, warn_bad_lines=True, encoding='iso8859_16',dtype=dtipo_campos,skiprows=1)


#filtrado de lineas de la medidas 
#III.5   Programas de apoyo en el sector vitivinicola
#III.4   Ayuda en el sector de las frutas y hortalizas
filter_list = ["III.5   Programas de apoyo en el sector vitivinicola", 
               "III.4   Ayuda en el sector de las frutas y hortalizas"]

PAC_2021_MIS_MEDIDAS_df =PAC_2021_df.loc[PAC_2021_df["MEDIDA"].isin(filter_list)]

```
