# Dashboard-de-Vendas-do-Xbox-com-Excel

cat <<'EOF' > README.md
# 📊 Dashboard de Vendas

## 📌 Descrição

Este projeto tem como objetivo a criação de um **dashboard de vendas**, com foco na **organização, tratamento e visualização de dados**.  
A proposta é transformar **dados brutos** em **informações visuais claras e úteis**, permitindo uma análise eficiente do desempenho de vendas e apoiando a **tomada de decisões baseada em dados**.

---

## 🎯 Objetivos do Projeto

- Organizar e tratar dados de vendas
- Criar visualizações claras e intuitivas
- Analisar o desempenho comercial
- Apoiar decisões estratégicas baseadas em dados

---

## 🧱 Estrutura do Projeto



---

## 📈 Indicadores Analisados

- Faturamento total
- Faturamento por período (mês)
- Faturamento por produto
- Faturamento por região

---

## ⚙️ Tecnologias Utilizadas

- Python 3
- Pandas
- Matplotlib
- Git e GitHub

---

## ▶️ Como Executar o Projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git



import pandas as pd
import matplotlib.pyplot as plt

# =========================
# EXTRAÇÃO
# =========================
arquivo = "/mnt/data/805d54f9-6d53-4246-bed7-4aa2da615923(A̳ssets).csv"
df = pd.read_csv(arquivo)

# =========================
# TRANSFORMAÇÃO
# =========================
# Ajuste os nomes das colunas se necessário
# Exemplo esperado:
# data, produto, quantidade, valor_unitario, vendedor, regiao

df["data"] = pd.to_datetime(df["data"])
df["faturamento"] = df["quantidade"] * df["valor_unitario"]
df["mes"] = df["data"].dt.to_period("M")

# =========================
# ANÁLISES
# =========================
faturamento_total = df["faturamento"].sum()
vendas_por_mes = df.groupby("mes")["faturamento"].sum()
vendas_por_produto = df.groupby("produto")["faturamento"].sum()
vendas_por_regiao = df.groupby("regiao")["faturamento"].sum()

print(f"Faturamento Total: R$ {faturamento_total:,.2f}")

# =========================
# VISUALIZAÇÕES
# =========================

# Faturamento por mês
plt.figure()
vendas_por_mes.plot(kind="bar")
plt.title("Faturamento por Mês")
plt.xlabel("Mês")
plt.ylabel("Faturamento (R$)")
plt.tight_layout()
plt.show()

# Faturamento por produto
plt.figure()
vendas_por_produto.plot(kind="bar")
plt.title("Faturamento por Produto")
plt.xlabel("Produto")
plt.ylabel("Faturamento (R$)")
plt.tight_layout()
plt.show()

# Faturamento por região
plt.figure()
vendas_por_regiao.plot(kind="bar")
plt.title("Faturamento por Região")
plt.xlabel("Região")
plt.ylabel("Faturamento (R$)")
plt.tight_layout()
plt.show()
