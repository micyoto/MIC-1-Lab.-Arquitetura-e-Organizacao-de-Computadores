# Diagrama da Arquitetura MIC-1

## Visão Geral dos Componentes

```
                           MIC-1 MICROPROCESSOR ARCHITECTURE
    
    ┌─────────────────────────────────────────────────────────────────────────────┐
    │                              CAMINHO DE DADOS                               │
    ├─────────────────────────────────────────────────────────────────────────────┤
    │                                                                             │
    │  ┌─────┐    ┌─────┐    ┌─────┐    ┌─────┐    ┌─────┐    ┌─────┐            │
    │  │ MAR │    │ MDR │    │ PC  │    │ SP  │    │ LV  │    │ CPP │            │
    │  └─────┘    └─────┘    └─────┘    └─────┘    └─────┘    └─────┘            │
    │      │          │          │          │          │          │              │
    │      └──────────┼──────────┼──────────┼──────────┼──────────┼──────────┐   │
    │                 │          │          │          │          │          │   │
    │  ┌─────┐    ┌─────┐    ┌─────┐  ┌─────────────┐ ┌─────────────────────┐│   │
    │  │ TOS │    │ OPC │    │  H  │  │     ALU     │ │      SHIFTER        ││   │
    │  └─────┘    └─────┘    └─────┘  │   32-bit    │ │     UNIT            ││   │
    │      │          │          │    │             │ │                     ││   │
    │      └──────────┼──────────┼────┤ ADD/SUB     │ │ SLL/SRA             ││   │
    │                 │          │    │ AND/OR/NOT  │ │                     ││   │
    │                 │          │    └─────────────┘ └─────────────────────┘│   │
    │                 │          │            │               │               │   │
    │    ┌────────────┼──────────┼────────────┼───────────────┼───────────────┘   │
    │    │            │          │            │               │                   │
    │    │     A-BUS (32-bit)    │            │               │                   │
    │    │                       │            │               │                   │
    │    │     B-BUS (32-bit)    │            │               │                   │
    │    │                       │            │               │                   │
    │    │     C-BUS (32-bit)    │            │               │                   │
    │    │                       │            │               │                   │
    │    └───────────────────────┼────────────┼───────────────┼───────────────────│
    │                            │            │               │                   │
    └────────────────────────────┼────────────┼───────────────┼───────────────────┘
                                 │            │               │
    ┌────────────────────────────┼────────────┼───────────────┼───────────────────┐
    │                       UNIDADE DE CONTROLE                                  │
    ├────────────────────────────┼────────────┼───────────────┼───────────────────┤
    │                            │            │               │                   │
    │  ┌─────────────────────────────────────────────────────────────────────┐   │
    │  │                    MICROPROGRAMA ROM                               │   │
    │  │                                                                     │   │
    │  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐                │   │
    │  │  │ DECODER     │  │ LOGIC UNIT  │  │ CONTROL     │                │   │
    │  │  │ 2x4         │  │             │  │ SIGNALS     │                │   │
    │  │  └─────────────┘  └─────────────┘  └─────────────┘                │   │
    │  └─────────────────────────────────────────────────────────────────────┘   │
    │                                                                             │
    └─────────────────────────────────────────────────────────────────────────────┘
    
    ┌─────────────────────────────────────────────────────────────────────────────┐
    │                              MEMÓRIA                                        │
    ├─────────────────────────────────────────────────────────────────────────────┤
    │                                                                             │
    │  ┌─────────────────────────┐         ┌─────────────────────────┐            │
    │  │    MEMÓRIA PRINCIPAL    │         │    MEMÓRIA DE CONTROLE  │            │
    │  │      (32KB)             │         │      (MICROPROGRAMA)    │            │
    │  │                         │         │                         │            │
    │  │  Instruções + Dados     │         │   Microinstruções       │            │
    │  │                         │         │                         │            │
    │  └─────────────────────────┘         └─────────────────────────┘            │
    │                                                                             │
    └─────────────────────────────────────────────────────────────────────────────┘
```

## Hierarquia de Componentes

```
                        MIC-1 COMPONENT HIERARCHY
    
    MIC-1 Processor (Top Level)
    │
    ├── Data Path
    │   ├── Registers (32-bit)
    │   │   ├── Register 8-bit (x4 components)
    │   │   │   └── Register 1-bit (x8 components)
    │   │   └── ...
    │   │
    │   ├── ALU (32-bit)
    │   │   ├── ALU 8-bit (x4 components)
    │   │   │   └── ALU 1-bit (x8 components)
    │   │   │       └── Full Adder 1-bit
    │   │   └── ...
    │   │
    │   └── Shifter Unit
    │       ├── SLL8 (Shift Left Logical)
    │       ├── SRA1 (Shift Right Arithmetic)
    │       └── Shifter Controller
    │
    ├── Control Unit
    │   ├── Decoder 2x4
    │   ├── Logic Unit
    │   └── Microprogram Counter
    │
    └── Memory Interface
        ├── MAR (Memory Address Register)
        └── MDR (Memory Data Register)
```

## Fluxo de Dados

```
    INSTRUCTION EXECUTION FLOW
    
    1. FETCH CYCLE
       PC → MAR → Memory → MDR → OPC
    
    2. DECODE CYCLE
       OPC → Control Unit → Microprogram Address
    
    3. EXECUTE CYCLE
       Registers → A-Bus, B-Bus → ALU/Shifter → C-Bus → Registers
    
    4. WRITEBACK CYCLE
       Result → Memory (if needed)
```

## Sinais de Controle

```
    CONTROL SIGNALS OVERVIEW
    
    ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
    │   CLOCK         │    │   ENABLE        │    │   SELECT        │
    │   - CLK         │    │   - REG_EN      │    │   - ALU_OP      │
    │   - RESET       │    │   - MEM_EN      │    │   - BUS_SEL     │
    │                 │    │   - SHIFT_EN    │    │   - REG_SEL     │
    └─────────────────┘    └─────────────────┘    └─────────────────┘
```
