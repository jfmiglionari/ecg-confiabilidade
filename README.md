# Confiabilidade de classificadores de arritmias em ECG entre bases de dados

**Avaliação da generalização e da confiabilidade de classificadores de arritmias cardíacas em eletrocardiogramas de 12 derivações.**

Projeto de pesquisa de mestrado em bioinformática aplicada à inteligência artificial, em fase de pré-projeto.

## Problema
Classificadores de ECG atingem alto desempenho quando treinados e testados na mesma base. Aplicados a outra instituição ou outro país, podem errar mais e, sobretudo, continuar declarando alta confiança. A literatura que estuda a troca de base mede principalmente o acerto; a que estuda incerteza raramente troca de base.

**Pergunta de pesquisa.** Como a mudança entre bases de dados de ECG afeta o desempenho, a calibração e a confiabilidade de classificadores de arritmias cardíacas, e em que medida técnicas de estimativa de incerteza podem reduzir previsões excessivamente confiantes?

> Escopo: este projeto não desenvolve uma ferramenta de diagnóstico clínico. O objetivo é avaliar cientificamente a confiabilidade dos classificadores.

## Abordagem
1. Seleção das bases públicas de ECG
2. Harmonização dos diagnósticos e pré-processamento
3. Separação por paciente e definição dos domínios
4. Treinamento dos classificadores de referência (ResNet 1D e um modelo mais simples)
5. Validação interna e externa entre bases
6. Avaliação da calibração e estimativa de incerteza (temperature scaling, deep ensembles, MC Dropout)
7. Análise de abstenção seletiva e comparação estatística

| Dimensão | Métricas |
|---|---|
| Desempenho | Macro-F1, AUROC, sensibilidade |
| Calibração | ECE, Brier score |
| Incerteza e abstenção | Curvas risco-cobertura |
| Estabilidade | Intervalos de confiança, repetição dos experimentos |

## Organização do repositório
| Pasta | Conteúdo |
|---|---|
| `docs/` | Visão geral, bases de dados, revisão da literatura, roadmap |
| `docs/decisoes/` | Registro de decisões técnicas (ADRs): contexto, opções e justificativa |
| `src/` | Código: dados, modelos, calibração, avaliação |
| `configs/` | Configurações dos experimentos (uma por experimento, versionada) |
| `experimentos/` | Descrição de cada experimento e como reproduzi-lo |
| `testes/` | Testes, a começar pelo mapeamento de rótulos entre bases |
| `dados/` | Não versionada: scripts e instruções para baixar das fontes oficiais |
| `resultados/` | Tabelas e figuras finais |

## Princípios
- **Reprodutibilidade:** dados só de fontes públicas, baixados por script; sementes fixas; cada resultado aponta para a configuração que o gerou.
- **Sem vazamento:** separação treino/teste por paciente, nunca por exame.
- **Decisão registrada:** toda escolha de método vira um ADR antes de virar código.
- **Rigor acima de quantidade:** poucos modelos, avaliados com repetição e intervalo de confiança.

## Status
Pré-projeto em elaboração. Veja `docs/roadmap.md`.

## Licença
MIT (código e documentação). As bases de dados seguem as licenças das fontes originais e não são redistribuídas aqui.
