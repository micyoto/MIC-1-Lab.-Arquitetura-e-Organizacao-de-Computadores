# MIC-1 Lab - Arquitetura e Organização de Computadores

Este projeto implementa os componentes fundamentais do microprocessador MIC-1 conforme descrito no livro "Arquitetura e Organização de Computadores" de Andrew S. Tanenbaum, utilizando o Quartus II 64-bit da Altera/Intel.

## 📋 Índice

- [Visão Geral](#visão-geral)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Componentes Implementados](#componentes-implementados)
- [Requisitos](#requisitos)
- [Como Usar](#como-usar)
- [Simulação](#simulação)
- [Estrutura de Arquivos](#estrutura-de-arquivos)
- [Contribuição](#contribuição)

## 🎯 Visão Geral

O MIC-1 (Microprocessor Implementation Computer - 1) é um microprocessador educacional projetado para demonstrar os conceitos fundamentais de arquitetura de computadores. Este projeto implementa todos os componentes essenciais usando diagramas de blocos (BDF - Block Diagram Files) no Quartus II.

![Arquitetura MIC-1](images/mic1_architecture.png)
*Diagrama completo da arquitetura MIC-1 - Caminho de dados e unidade de controle*

### Características Principais:
- **Arquitetura**: 32 bits
- **Tecnologia**: Cyclone II FPGA
- **Metodologia**: Bottom-up (componentes de 1 bit → 8 bits → 32 bits)
- **Simulação**: ModelSim-Altera com arquivos de forma de onda (VWF)

> 📋 **Nota**: Para visualizar os diagramas detalhados da arquitetura, consulte o arquivo [ARCHITECTURE_DIAGRAM.md](ARCHITECTURE_DIAGRAM.md)

## 🏗️ Estrutura do Projeto

```
MIC1/
├── 📁 Componentes Básicos (1-bit)
│   ├── full_adder_1bit.bdf       # Somador completo de 1 bit
│   ├── register_1bit.bdf         # Registrador de 1 bit
│   └── ula_1bit.bdf              # ULA de 1 bit
│
├── 📁 Componentes Intermediários (8-bit)
│   ├── register_8bit.bdf         # Registrador de 8 bits
│   └── ula_8bit.bdf              # ULA de 8 bits
│
├── 📁 Componentes Avançados (32-bit)
│   ├── register_32bit.bdf        # Registrador de 32 bits
│   └── ula_32bit.bdf             # ULA de 32 bits
│
├── 📁 Componentes de Controle
│   ├── decoder_2x4.bdf           # Decodificador 2x4
│   ├── logic_unit.bdf            # Unidade Lógica
│   ├── shifter.bdf               # Unidade de Deslocamento
│   ├── sra1.bdf                  # Shift Right Arithmetic (1 bit)
│   └── sll8.bdf                  # Shift Left Logical (8 bits)
│
├── 📁 Arquivos de Simulação
│   ├── *.vwf                     # Arquivos de forma de onda
│   └── *.vwf.temp                # Arquivos temporários de simulação
│
└── 📁 Arquivos do Projeto
    ├── MIC1.qpf                  # Arquivo do projeto Quartus
    ├── MIC1.qsf                  # Configurações do projeto
    └── *.bsf                     # Arquivos de símbolo
```

## ⚙️ Componentes Implementados

![Hierarquia de Componentes](images/component_hierarchy.png)
*Hierarquia dos componentes implementados - do 1-bit ao 32-bit*

### 1. **Somador Completo (Full Adder) - 1 bit**
- **Arquivo**: `full_adder_1bit.bdf`
- **Função**: Realiza soma binária de dois bits com carry
- **Entradas**: A, B, Cin
- **Saídas**: Sum, Cout

![Full Adder](images/full_adder_diagram.png)
*Diagrama lógico do somador completo de 1 bit*

### 2. **Registrador - 1, 8 e 32 bits**
- **Arquivos**: `register_1bit.bdf`, `register_8bit.bdf`, `register_32bit.bdf`
- **Função**: Armazenamento temporário de dados
- **Controle**: Clock, Enable, Reset
- **Aplicação**: Registradores do MIC-1 (MAR, MDR, PC, SP, LV, CPP, TOS, OPC, H)

![Registradores](images/registers_diagram.png)
*Estrutura dos registradores de 1, 8 e 32 bits*

### 3. **ULA (Unidade Lógico-Aritmética)**
- **Arquivos**: `ula_1bit.bdf`, `ula_8bit.bdf`, `ula_32bit.bdf`
- **Operações Aritméticas**: Soma, Subtração
- **Operações Lógicas**: AND, OR, NOT
- **Função**: Coração computacional do processador

![ULA](images/alu_diagram.png)
*Arquitetura da ULA de 32 bits com operações aritméticas e lógicas*

### 4. **Decodificador 2x4**
- **Arquivo**: `decoder_2x4.bdf`
- **Função**: Converte 2 bits de entrada em 4 linhas de saída
- **Aplicação**: Decodificação de sinais de controle

### 5. **Unidade de Deslocamento (Shifter)**
- **Arquivos**: `shifter.bdf`, `sra1.bdf`, `sll8.bdf`
- **Operações**: 
  - SLL (Shift Left Logical)
  - SRA (Shift Right Arithmetic)
- **Função**: Operações de deslocamento de bits

![Shifter](images/shifter_diagram.png)
*Unidade de deslocamento com operações SLL e SRA*

### 6. **Unidade Lógica**
- **Arquivo**: `logic_unit.bdf`
- **Função**: Operações lógicas complexas
- **Integração**: Combina múltiplas operações lógicas

## 🔧 Requisitos

### Software Necessário:
- **Quartus II 64-bit** (versão 13.0 SP1 ou superior)
- **ModelSim-Altera** (para simulação)
- **Windows** (compatível com o ambiente de desenvolvimento)

### Hardware Recomendado:
- **FPGA**: Cyclone II (configurado no projeto)
- **RAM**: Mínimo 4GB
- **Processador**: x64 compatível

## 🚀 Como Usar

### 1. **Abertura do Projeto**
```bash
# Abrir o Quartus II
# File → Open Project → Selecionar MIC1.qpf
```

### 2. **Compilação**
```bash
# No Quartus II:
# Processing → Start Compilation (Ctrl+L)
```

### 3. **Simulação**
```bash
# Abrir arquivo .vwf desejado
# Simulation → Start Simulation
# Analisar formas de onda no ModelSim
```

### 4. **Síntese para FPGA**
```bash
# Tools → Programmer
# Configurar dispositivo Cyclone II
# Start Programming
```

## 📊 Simulação

O projeto inclui arquivos de simulação (.vwf) para cada componente:

![Simulação](images/simulation_waveforms.png)
*Exemplo de formas de onda da simulação da ULA de 8 bits*

### Testes Implementados:
- **ULA 8-bit**: 
  - `ULA_8bit_ADD.vwf` - Teste de soma
  - `ULA_8bit_AND.vwf` - Teste AND
  - `ULA_8bit_OR.vwf` - Teste OR
  - `ULA_8bit_CONSTANTS.vwf` - Teste com constantes

- **Registradores**:
  - `register_8bit.vwf` - Teste de armazenamento
  - `register_32bit.vwf` - Teste de registrador completo

- **Componentes Individuais**:
  - Cada componente possui seu arquivo `.vwf` correspondente

### Como Interpretar as Simulações:

![Guia de Simulação](images/simulation_guide.png)
*Guia para interpretação das formas de onda no ModelSim*

1. **Sinais de Clock**: Identificam ciclos de operação
2. **Sinais de Enable**: Controlam quando componentes estão ativos  
3. **Dados de Entrada**: Valores aplicados aos componentes
4. **Dados de Saída**: Resultados das operações
5. **Sinais de Status**: Flags como carry, zero, overflow

## 📁 Estrutura de Arquivos

| Extensão | Descrição |
|----------|-----------|
| `.bdf` | Block Diagram File - Diagrama esquemático |
| `.bsf` | Block Symbol File - Arquivo de símbolo |
| `.vwf` | Vector Waveform File - Arquivo de simulação |
| `.qpf` | Quartus Project File - Arquivo do projeto |
| `.qsf` | Quartus Settings File - Configurações |
| `.qws` | Quartus Workspace File - Área de trabalho |

### Diretórios do Sistema:
- **`db/`**: Base de dados do projeto (arquivos de compilação)
- **`incremental_db/`**: Compilação incremental
- **`output_files/`**: Arquivos de saída da síntese
- **`simulation/`**: Arquivos de simulação do ModelSim

## 🎓 Conceitos Educacionais

Este projeto demonstra:

1. **Hierarquia de Design**: Bottom-up approach
2. **Reutilização de Componentes**: Blocos de 1-bit para construir sistemas maiores
3. **Simulação e Verificação**: Testes extensivos de cada componente
4. **Síntese para Hardware**: Implementação real em FPGA

## 📚 Referência

Baseado no livro:
**"Arquitetura e Organização de Computadores"**
*Andrew S. Tanenbaum*

### Capítulos Relevantes:
- Capítulo 4: Nível de Microarquitetura
- Seção 4.1: Exemplo de Microarquitetura: MIC-1

## 🤝 Contribuição

Para contribuir com o projeto:

1. Fork o repositório
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto é educacional e segue os termos da licença Altera/Intel para ferramentas de desenvolvimento.

---

*Projeto desenvolvido como material de apoio para disciplinas de Arquitetura e Organização de Computadores*
