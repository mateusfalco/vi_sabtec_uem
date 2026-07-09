# Desafio Prático: Análise de Microbioma (FMT) com nf-core/ampliseq

Bem-vindos à atividade complementar do minicurso **Bioinformática Reprodutível: Automatizando pipelines com Nextflow e nf-core** (VI Semana Acadêmica de Biotecnologia - CABTEC/UEM).

Esta atividade prática tem como objetivo consolidar os conceitos vistos em aula. Você irá executar de forma autônoma o mesmo pipeline profissional demonstrado na teoria para avaliar a composição taxonômica de uma amostra de microbioma (utilizando dados de sequenciamento amplicon 16S).

> **⚠️ ATENÇÃO - REQUISITO PARA CERTIFICAÇÃO**
> A realização desta atividade e o preenchimento do formulário de avaliação são **obrigatórios** para a validação da sua carga horária e emissão do certificado de participação.
> 
> **📅 Prazo final para envio:** 09 de julho de 2026, até às 23h00.
> **🔗 Link para envio (Formulário):** [FORMULÁRIO](https://forms.gle/L1rAmGavWcmDMPvo9)

---

## Passo 1: Preparação do Ambiente de Trabalho

Para garantir que todos tenham a mesma experiência sem depender do hardware local, utilizaremos as ferramentas em nuvem abordadas em aula.

1. Faça login na sua conta do **GitHub**.
2. Acesse o repositório do minicurso: `https://github.com/mateusfalco/start_bioinfo_26`.
3. Abra o repositório em seu ambiente de desenvolvimento em nuvem (recomendamos o **GitHub Codespaces**).
4. Aguarde o ambiente carregar completamente e abra o terminal integrado.

## Passo 2: Criação do Arquivo de Entrada (Samplesheet)

Para o pipeline entender quais amostras processar, precisamos criar uma planilha de mapeamento. Analisaremos o dataset de acesso público **SRR34798367**.

1. No diretório principal do seu ambiente, crie um arquivo chamado `samplesheet.csv`.
2. Copie e cole o texto exato abaixo dentro do arquivo e salve:

```csv
sampleID,forwardReads,reverseReads,run
SRR38093667,,,
```

## Passo 3: Execução do Pipeline Nextflow

Agora vamos acionar o Nextflow. Ele cuidará do controle de qualidade (FastQC), da inferência de variantes de amplicon (DADA2) e da classificação taxonômica através do pipeline ampliseq.

Copie o comando abaixo, cole no seu terminal e pressione Enter:

```bash
nextflow run nf-core/ampliseq \
  -r 2.18.0 \
  -profile docker \
  -c nextflow.config \
  --input samplesheet-extra.csv \
  --FW_primer GTGYCAGCMGCCGCGGTAA \
  --RV_primer GGACTACNVGGGTWTCTAAT \
  --outdir ./atividade \
```
Nota: Os parâmetros de primer acima correspondem à região V4 do gene 16S rRNA, padrão ouro para estudos de microbioma).

## Passo 4: Análise dos Resultados

Quando a execução terminar com sucesso, uma nova pasta chamada resultados_ampliseq aparecerá. O pipeline ampliseq gera saídas muito ricas, incluindo gráficos em PDF/HTML de diversidade.

   1. Navegue até o diretório resultados_ampliseq/multiqc/.

   2. Faça o download do arquivo multiqc_report.html para o seu computador e abra-o no navegador.

   3. Explore as métricas de qualidade das leituras e a porcentagem de sequências retidas após a filtragem do DADA2.

   4. Navegue também pela pasta resultados_ampliseq/qiime2/ ou dada2/ para visualizar as tabelas de abundância taxonômica.

## Passo 5: Avaliação e Envio

Após analisar criticamente o seu relatório, acesse o formulário oficial e responda às questões sobre os resultados que você obteve.

🔗 [Formulário de Avaliação e Envio de Atividade - Clique Aqui](https://forms.gle/L1rAmGavWcmDMPvo9)

Bom trabalho e excelente análise!
