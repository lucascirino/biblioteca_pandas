# biblioteca_pandas

Maio quantidade de vendas por departamentp = 
qtd_vendas_dpto = preço_correto.groupby('Nome_Departamento').idcompra.nunique().sort_values(ascending=False).reset_index()

Média de preço com frete por nome de departamento =
média_por_departamento = round(preço_correto.groupby('Nome_Departamento')['Preço_com_frete'].mean('Preço_com_frete').sort_values(ascending=False).reset_index(),2)

Quantidade de vendas por mês = 
preço_correto.groupby('mes').idcompra.nunique().sort_values(ascending=False).reset_index()

Média de renda por canal de venda =
renda_por_canal = round(vendas_cliente.groupby('idcanalvenda') ['renda'].mean().sort_values(ascending=False).reset_index(),2)

Média de idade por bandeira =
idade_por_bandeira= round(vendas_cliente.groupby('bandeira')['idade'].mean().sort_values(ascending=False).reset_index(),0)

Todas as vendas sem UF , devem ser substituídas por 'MS'
Preço não pode ser menor que preço com frete.


Funções para relembrar 

vendas.groupby('idcanalvenda').idcompra.nunique()
Groupby realiza o agrupamento , já o nunique conta os valores distintos , nesse caso está utilizando a coluna idcompra para isso.

vendas['idcanalvenda'].str.replace ('APP','Aplicativo') 
O .str é utilizado porque a coluna tem como tipo Object , e porque permite a utilização dos métodos em string, como o replace. Trocando APP por Aplicativo.

vendas['Nome_Departamento'] = vendas['Nome_Departamento'].str.replace(' ','_').str.replace(',','')
usando 2 condições para replace,  ' ' por _ e , por ''

vendas[vendas['estado'].isnull()]
Aqui vemos as células sem valor em estado.

vendas['estado']= vendas['estado'].fillna('MS')
Aqui preenchemos os valores nulos por 'MS' utilizando fillna

vendas['Preço'].fillna(media_precos,inplace=True)
Aqui utilizamos uma variável para preencher os nulos , o inplace=True serve para substituir direto na base vendas.

preço_errado = vendas.query("Preço>Preço_com_frete")
Utilizando .query para filtrar de acordo com a condição passada.

preço_correto["mes"] = preço_correto["Data"].dt.month
Foi utilizado a biblioteca datetime para trazer da coluna Data, apenas os meses e criar uma coluna 'mes'

clientes['renda'] = clientes['renda'].astype(float)
Alteração do tipo de dados da coluna renda para float

vendas_cliente = preço_correto.merge(clientes,how='left', on='cliente_Log')
merge é fazer um join para união das duas tabelas, on é a chave igual entre as duas tabelas.


Gráficos.

fig = plt.figure(figsize=(4,3))   # tamanho da figura
plt.bar(idade_por_bandeira['bandeira'],idade_por_bandeira['idade'],color='green')  # tipo de gráfico
plt.xlabel('Bandeira') # nome do eixo x
plt.ylabel('Média de Idade') # nome do eixo y
plt.title('Idade Média por Bandeira',loc='center',fontsize=15, fontweight = 'bold', color='black');  # configurações do Título


fig = plt.figure(figsize=(14,6)) # tamanho da figura
plt.xlabel('Data da venda') # nome do eixo x
plt.ylabel('Qtd. de vendas') # nome do eixo y
x= vendas_por_data['Data'] # variável para o eixo x
y= vendas_por_data['idcompra'] # variável para o eixo y
plt.plot(x,y, color='black' , linewidth ='2')  # tipo de gráfico
plt.show()  # Comando para exibir


utilizando a biblioteca do plotly
Exemplo 1 :
px.bar (idade_por_bandeira , x='bandeira',y='idade' ) 

Exemplo 2 :
px.line(vendas_por_data,x='Data',y='idcompra')

Exemplo 3 :
px.bar(média_por_departamento,x='Nome_Departamento',y='Preço_com_frete')
