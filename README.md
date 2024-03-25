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
