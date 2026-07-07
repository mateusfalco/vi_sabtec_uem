#  Desafio Prático: Vigilância Genômica com [nf-core/viralrecon](https://nf-co.re/viralrecon/3.0.0)

Bem-vindos à atividade complementar do curso **Bioinformática Reprodutível: Automatizando pipelines com Nextflow e nf-core** (VI Semana Acadêmica de Biotecnologia - CABTEC/UEM).

Esta atividade prática tem como objetivo consolidar os conceitos vistos em aula, permitindo que você execute de forma autônoma um pipeline profissional de bioinformática para identificar variantes do vírus SARS-CoV-2 a partir de dados brutos de sequenciamento.

> **⚠️ ATENÇÃO - REQUISITO PARA CERTIFICAÇÃO**
> A realização desta atividade e o preenchimento do formulário de avaliação são **obrigatórios** para a validação da sua carga horária e emissão do certificado de participação.
> 
> **📅 Prazo final para envio:** 09 de julho de 2026, até às 23h00.
> **🔗 Link para envio (Formulário):** [FORMULÁRIO](https://forms.gle/t2n81D7dcCGzx5RJ6)

---

## Passo 1: Preparação do Ambiente de Trabalho

Para garantir que todos tenham a mesma experiência sem depender do hardware local, utilizaremos as ferramentas em nuvem abordadas em aula.

1. Faça login na sua conta do **GitHub**.
2. Acesse o repositório do minicurso: `https://github.com/mateusfalco/vi_sabtec_uem`.
3. Abra o repositório em seu ambiente de desenvolvimento em nuvem (recomendamos o uso do **GitHub Codespaces**).
4. Aguarde o ambiente carregar completamente e abra o terminal integrado.

## Passo 2: Criação do Arquivo de Entrada (Samplesheet)

Pipelines profissionais precisam de um arquivo de mapeamento (*samplesheet*) para entender a origem e a organização dos dados. Para este desafio, utilizaremos a amostra pública de acesso **SRR28464539**.

1. No diretório principal do seu ambiente, crie um arquivo chamado `samplesheet_extra.csv`.
2. Copie e cole o texto exato abaixo dentro do arquivo e salve:

```csv
sample,fastq_1,fastq_2
SRR28464539,,,
```

## Passo 3: Execução do Pipeline Nextflow

Com o ambiente e a amostra configurados, é hora de rodar a análise. O Nextflow cuidará do download do pipeline, da gestão dos contêineres e da orquestração das tarefas (como FastQC, alinhamento e variant calling).

Copie o comando abaixo, cole no seu terminal e pressione Enter:

```bash
nextflow run nf-core/viralrecon \
  -profile docker \
  --input samplesheet.csv \
  --outdir ./resultados_viralrecon \
  --platform illumina \
  --protocol amplicon \
  --genome 'NC_045512.2' \
  --skip_kraken2
```
Dica: O processo levará alguns minutos. Observe o log na tela prestando atenção em como as tarefas são submetidas e concluídas.

## Passo 4: Análise dos Resultados

Quando a execução terminar 100% com sucesso, uma nova pasta chamada resultados_viralrecon aparecerá no seu menu lateral.

   1. Navegue até o diretório resultados_viralrecon/multiqc/illumina/.

   2. Faça o download do arquivo multiqc_report.html para o seu computador.

   3. Abra este arquivo em qualquer navegador web.

   4. Explore as métricas de qualidade interativas, a taxa de alinhamento e o sumário de variantes encontradas.

## Passo 5: Avaliação e Envio

Após analisar criticamente o seu relatório MultiQC, acesse o formulário oficial e responda às questões propostas sobre os resultados que você obteve.

[Formulário de Avaliação e Envio de Atividade - Clique Aqui](https://forms.gle/t2n81D7dcCGzx5RJ6)

Bom trabalho e excelente análise!
