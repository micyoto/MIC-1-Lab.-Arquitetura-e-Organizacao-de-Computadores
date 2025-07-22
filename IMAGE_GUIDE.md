# Guia de Imagens para o Projeto MIC-1

Este arquivo contém sugestões para criar as imagens referenciadas nos arquivos README do projeto MIC-1.

## 📷 Imagens Necessárias

### 1. **mic1_architecture.png**
**Descrição**: Diagrama completo da arquitetura MIC-1
**Conteúdo**:
- Caminho de dados com todos os 9 registradores (MAR, MDR, PC, SP, LV, CPP, TOS, OPC, H)
- ULA de 32 bits no centro
- Unidade de deslocamento (Shifter)
- Três barramentos (A-bus, B-bus, C-bus)
- Unidade de controle com microprograma
- Conexões entre componentes

**Ferramentas sugeridas**: Draw.io, Visio, ou captura de tela do Quartus II Block Editor

### 2. **component_hierarchy.png**
**Descrição**: Hierarquia dos componentes implementados
**Conteúdo**:
- Árvore mostrando como componentes de 1-bit se combinam para formar 8-bit e 32-bit
- Relação entre Full Adder → ULA 1-bit → ULA 8-bit → ULA 32-bit
- Relação entre Register 1-bit → Register 8-bit → Register 32-bit
- Código de cores para diferentes níveis de hierarquia

### 3. **full_adder_diagram.png**
**Descrição**: Diagrama lógico do somador completo
**Conteúdo**:
- Portas lógicas (XOR, AND, OR)
- Entradas: A, B, Cin
- Saídas: Sum, Cout
- Tabela verdade opcional
- Equações lógicas: Sum = A⊕B⊕Cin, Cout = AB + Cin(A⊕B)

### 4. **registers_diagram.png**
**Descrição**: Estrutura dos registradores
**Conteúdo**:
- Flip-flops D conectados
- Sinais de controle (Clock, Enable, Reset)
- Comparação entre registradores de 1, 8 e 32 bits
- Diagrama de temporização básico

### 5. **alu_diagram.png**
**Descrição**: Arquitetura da ULA
**Conteúdo**:
- Bloco funcional da ULA
- Entradas A e B (32 bits cada)
- Sinais de controle para selecionar operação
- Saídas (Resultado + flags)
- Lista de operações suportadas (ADD, SUB, AND, OR, NOT)

### 6. **shifter_diagram.png**
**Descrição**: Unidade de deslocamento
**Conteúdo**:
- Blocos SLL8 e SRA1
- Multiplexadores para seleção de operação
- Exemplos visuais de deslocamento (antes/depois)
- Sinais de controle

### 7. **simulation_waveforms.png**
**Descrição**: Exemplo de formas de onda
**Conteúdo**:
- Captura de tela do ModelSim
- Formas de onda da simulação ULA_8bit_ADD.vwf
- Sinais claramente rotulados
- Exemplo de operação de soma sendo executada

### 8. **simulation_guide.png**
**Descrição**: Guia para interpretação de simulações
**Conteúdo**:
- Legenda dos tipos de sinais
- Escala de tempo
- Como identificar transições válidas
- Explicação dos diferentes tipos de linha (clock, dados, controle)

## 🛠️ Como Criar as Imagens

### Opção 1: Screenshots do Quartus II
1. Abrir arquivos .bdf no Quartus II Block Editor
2. Usar Zoom para ajustar visualização
3. Capturar tela com qualidade alta
4. Editar em ferramenta de imagem para adicionar anotações

### Opção 2: Diagramas Customizados
1. **Draw.io** (https://app.diagrams.net/):
   - Gratuito e online
   - Templates de circuitos digitais
   - Exportação em PNG de alta qualidade

2. **Microsoft Visio**:
   - Ferramentas profissionais de diagramação
   - Templates de engenharia

3. **Lucidchart**:
   - Colaborativo e baseado na web
   - Good para diagramas técnicos

### Opção 3: Screenshots do ModelSim
1. Executar simulações no ModelSim
2. Configurar janela de ondas adequadamente
3. Capturar telas de alta resolução
4. Editar para destacar pontos importantes

## 📐 Especificações Técnicas das Imagens

### Resolução e Formato:
- **Formato**: PNG (para melhor qualidade)
- **Resolução**: Mínimo 1200x800 pixels
- **DPI**: 300 DPI para impressão, 72 DPI para web

### Estilo Visual:
- **Cores**: Use cores consistentes (azul para dados, vermelho para controle, verde para clock)
- **Fonte**: Arial ou similar, tamanho legível
- **Contraste**: Alto contraste para facilitar leitura
- **Anotações**: Setas e labels claros

### Organização dos Arquivos:
```
images/
├── mic1_architecture.png
├── component_hierarchy.png
├── full_adder_diagram.png
├── registers_diagram.png
├── alu_diagram.png
├── shifter_diagram.png
├── simulation_waveforms.png
└── simulation_guide.png
```

## ✅ Lista de Verificação

Para cada imagem criada, verificar:

- [ ] Resolução adequada (mínimo 1200x800)
- [ ] Texto legível em diferentes tamanhos
- [ ] Cores consistentes com o padrão do projeto
- [ ] Elementos importantes destacados
- [ ] Nome do arquivo correto
- [ ] Formato PNG
- [ ] Tamanho de arquivo otimizado (< 2MB por imagem)

## 🎨 Paleta de Cores Sugerida

- **Dados**: #2E86C1 (Azul)
- **Controle**: #E74C3C (Vermelho)
- **Clock**: #27AE60 (Verde)
- **Componentes**: #F39C12 (Laranja)
- **Conexões**: #34495E (Cinza escuro)
- **Background**: #FFFFFF (Branco)
- **Texto**: #2C3E50 (Cinza muito escuro)

## 📝 Notas Adicionais

1. **Consistência**: Mantenha estilo visual consistente em todas as imagens
2. **Acessibilidade**: Use contraste adequado para leitura
3. **Escalabilidade**: Imagens devem ser legíveis em diferentes tamanhos
4. **Atualização**: Mantenha imagens atualizadas conforme projeto evolui

---

*Este guia ajuda a criar uma documentação visual profissional e educativa para o projeto MIC-1*
