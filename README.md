# Calculadora de Preço de Software – ADA EJ

Uma ferramenta interativa para estimar o valor de projetos de software, desenvolvida para a **ADA EJ** (Empresa Júnior de Tecnologia). A calculadora considera horas técnicas, custos de infraestrutura, alocação da meta de faturamento e mensalidade estimada, gerando uma proposta transparente e profissional.

![Preview da calculadora](https://via.placeholder.com/800x400?text=Calculadora+ADA+EJ)  
*(Substitua pela imagem real, se disponível)*

---

## 🚀 Funcionalidades

- **Cálculo automático** do preço total do projeto com base em:
  - Meta de faturamento e período
  - Valor da hora técnica
  - Tecnologia escolhida (AWS, Heroku, GitHub Pages)
  - Complexidade do projeto (5 níveis)
  - Datas de início e término
  - Cotação do dólar (para custos em USD)
- **Detalhamento** do custo:
  - Desenvolvimento (horas × valor/hora)
  - Infraestrutura (hospedagem, conforme tecnologia e complexidade)
  - Alocação proporcional da meta de faturamento
- **Mensalidade estimada** para o cliente (baseada em custo de hospedagem + percentual de manutenção)
- **Validação de formulário** em tempo real
- **Design responsivo** e moderno com ícones Lucide

---

## 🛠️ Tecnologias Utilizadas

- **HTML5** – Estrutura semântica  
- **CSS3** – Estilização customizada com variáveis CSS e layout responsivo  
- **JavaScript (Vanilla)** – Lógica de cálculo, manipulação do DOM e validação  
- **Lucide Icons** – Biblioteca de ícones open-source  
- **date-fns** – Biblioteca para manipulação de datas (cálculo de meses entre datas)

> **Observação:** O código é totalmente autossuficiente em um único arquivo HTML, sem dependências externas além das bibliotecas carregadas via CDN.

---

## 📦 Como Usar

1. Faça o download do arquivo `calculo_precos_ada.html`.
2. Abra-o em qualquer navegador moderno (Chrome, Firefox, Edge, etc.).
3. Preencha todos os campos do formulário:
   - **Meta de faturamento** – valor total esperado no período definido.
   - **Período da meta** – em meses (ex.: 12 para anual).
   - **Valor da hora técnica** – quanto custa 1 hora de desenvolvimento.
   - **Cotação do Dólar** – valor atual do USD em BRL.
   - **Tecnologia** – selecione uma das opções (AWS, Heroku, GitHub Pages).
   - **Complexidade** – de *Baixa* a *Absurdamente complexa* (impacta horas/mês e custo de infra).
   - **Datas** – início e término do projeto.
4. Clique em **“Calcular preço”**.
5. Veja o resultado detalhado no painel à direita, incluindo:
   - Preço total estimado
   - Custo de desenvolvimento, infraestrutura e alocação da meta
   - Mensalidade sugerida para o cliente

---

## 🧩 Estrutura do Projeto

```
calculo_precos_ada.html
├── <head>
│   ├── Meta tags e título
│   ├── CDN: Lucide Icons + date-fns
│   └── Estilos CSS (reset, layout, componentes)
├── <body>
│   ├── Hero (cabeçalho com chamada)
│   ├── Main
│   │   ├── Formulário (card esquerdo)
│   │   │   ├── Dados financeiros (meta, período, valor hora, cotação)
│   │   │   ├── Tecnologia (radio cards)
│   │   │   ├── Complexidade (select)
│   │   │   ├── Datas
│   │   │   └── Botão de cálculo
│   │   └── Resultado (card direito)
│   │       ├── Preço total
│   │       ├── Detalhamento dos custos
│   │       └── Mensalidade estimada
│   └── Scripts JS
│       ├── Configuração de tecnologias e complexidades
│       ├── Renderização dinâmica dos campos
│       ├── Lógica de cálculo e validação
│       ├── Inicialização de ícones e valores padrão
└── (Fim)
```

---

## ⚙️ Personalização

### Tecnologias e custos de infraestrutura
Os dados estão no array `tecnologias` (linhas ~310-344). Cada tecnologia possui um `custoMap` que relaciona a complexidade com um custo mensal em **dólares** (USD). Para adicionar ou modificar uma tecnologia:

```javascript
{ 
  id: 'aws', 
  label: 'AWS', 
  icone: 'cpu',
  custoMap: {
    baixa: 45,
    media: 100,
    // ...
  }
}
```

### Complexidades e horas por mês
As complexidades estão no array `complexidades` (linhas ~346-352). O campo `horasPorMes` define a carga horária estimada para cada nível:

```javascript
{ id: 'baixa', label: 'Baixa', horasPorMes: 40 }
```

### Percentuais para mensalidade
No cálculo da mensalidade, é usado um percentual sobre o custo de desenvolvimento, definido no objeto `percentuais` (linha ~426-432). Ajuste conforme necessário.

---

## 📝 Observações

- O cálculo da **mensalidade** é uma estimativa simplificada: `mensalidade = custoMensalHospedagem + (custoDesenvolvimento * percentualComplexidade)`. Pode ser ajustada conforme a política da empresa.
- A **cotação do dólar** é usada para converter os custos de infraestrutura (definidos em USD) para BRL.
- As **datas** são validadas para garantir que a data de término seja posterior à data de início.
- O formulário possui **validação básica** (campos obrigatórios, valores positivos). Mensagens de erro são exibidas abaixo de cada campo.

---

## 👥 Contribuição

Sugestões e melhorias são bem-vindas! Sinta-se à vontade para adaptar o código às necessidades da sua empresa júnior. Para contribuir:

1. Faça um fork do repositório
2. Crie uma branch com sua feature (`git checkout -b feature/nova-feature`)
3. Commit suas alterações (`git commit -m 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/nova-feature`)
5. Abra um Pull Request

---

## 📄 Licença

Este projeto é de uso livre para fins educacionais e empresariais. Sinta-se à vontade para utilizá-lo e modificá-lo conforme necessário.

---

Desenvolvido com ❤️ para a **ADA EJ**.