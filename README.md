# Tutorial de Comandos Básicos do Bash Aplicados à Genômica

Este tutorial tem como objetivo ensinar comandos básicos do bash aplicados em um contexto de bioinformática, utilizando uma estrutura de diretórios e arquivos relacionados à genômica.
O minicurso pertence à XXVIII edição da SEBIO (Semana da Biologia) na UNiversidade Estadual do Centro Oeste (Unicentro/PR).

<p align="center">
  <img src="images/sebio.jpeg" alt="XXVIIISEBIO" width="50%">
</p>


## Estrutura de Diretórios e Arquivos

Os exercícios serão baseados na seguinte estrutura de diretórios:

```
bioinfo_exercicies
├── chromossome.txt
├── dna
│   ├── dna.fasta
│   └── dnaX.fasta
│   └── rna.fasta
├── dnaY.fasta
├── protein
│   ├── protein.fasta
│   ├── proteinX.fasta
│   └── proteinY.fasta
└── rna
└── chrom
fastq
├── 76_S2_L001_R1_001.fastq.gz
├── AM_S5_L001_R1_001.fastq.gz
└── P1B-16S_S6_L001_R2_001.fastq.gz
genes.vcf
scripts
└── first.sh
```

## Exercícios

### 1. Navegação no Sistema de Arquivos

#### 1.1. Exibir uma Mensagem no Terminal
Use o comando `echo` para exibir a mensagem "Bem-vindo ao tutorial de bash aplicado à bioinformática":

```bash
echo "Bem-vindo ao tutorial de bash aplicado à bioinformática"
```

#### 1.2. Mostrar o Diretório Atual
O comando `pwd` mostra o caminho do diretório atual:

```bash
pwd
```

#### 1.3. Navegar Entre Diretórios
Use o comando `cd` para navegar para o diretório `bioinfo_exercicies/dna`:

```bash
cd bioinfo_exercicies/dna
```

Use `cd ..` para voltar ao diretório pai (`bioinfo_exercicies`):

```bash
cd ..
```

### 2. Listagem de Arquivos

#### 2.1. Listar o Conteúdo de um Diretório
Liste o conteúdo do diretório `bioinfo_exercicies` usando o comando `ls`:

```bash
ls bioinfo_exercicies
```

Liste o conteúdo com detalhes, incluindo arquivos ocultos e tamanhos legíveis:

```bash
ls -lah bioinfo_exercicies
```

### 3. Download de Arquivos

#### 3.1. Baixar um Arquivo Usando `wget`
Baixe um arquivo de exemplo de sequenciamento:

```bash
wget http://example.com/sequencing_data.fastq.gz -P fastq/
```

### 4. Estrutura de Diretórios

#### 4.1. Visualizar a Estrutura de Diretórios
Use o comando `tree` para visualizar a estrutura de diretórios:

```bash
tree bioinfo_exercicies
```

#### 4.2. Criar um Novo Diretório
Crie um diretório chamado `results`:

```bash
mkdir results
```

### 5. Manipulação de Arquivos

#### 5.1. Copiar Arquivos
Copie o arquivo `chromossome.txt` para o diretório `results`:

```bash
cp bioinfo_exercicies/chromossome.txt results/
```

#### 5.2. Mover Arquivos
Movimente o arquivo `genes.vcf` para o diretório `results`:

```bash
mv genes.vcf results/
```

#### 5.3. Remover Arquivos
Remova o arquivo `results/genes.vcf`:

```bash
rm results/genes.vcf
```

### 6. Visualização de Conteúdo de Arquivos

#### 6.1. Exibir as Primeiras e Últimas Linhas de um Arquivo
Exiba as primeiras 10 linhas do arquivo `dna.fasta`:

```bash
head bioinfo_exercicies/dna/dna.fasta
```

Exiba as últimas 10 linhas do arquivo `protein.fasta`:

```bash
tail bioinfo_exercicies/protein/protein.fasta
```

#### 6.2. Concatenar e Exibir Conteúdo de Arquivos
Use `cat` para exibir o conteúdo do arquivo `rna.fasta`:

```bash
cat bioinfo_exercicies/rna/rna.fasta
```

#### 6.3. Criar um Arquivo Vazio
Use `touch` para criar um novo arquivo chamado `empty.txt` no diretório `results`:

```bash
touch results/empty.txt
```

### 7. Uso de `grep`, `pipe` e `nano`

#### 7.1. Procurar Padrões em Arquivos com `grep` e Usar `pipe`
Use o comando `grep` para procurar pela sequência "ATGC" no arquivo `dna.fasta`:

```bash
grep "ATGC" bioinfo_exercicies/dna/dna.fasta
```

Combine o comando `grep` com `pipe` (`|`) para contar o número de ocorrências da sequência "ATGC":

```bash
grep "ATGC" bioinfo_exercicies/dna/dna.fasta | wc -l
```

#### 7.2. Editar Arquivos Usando `nano`
Abra o arquivo `first.sh` no editor de texto `nano`:

```bash
nano scripts/first.sh
```

### 8. Criação de Scripts

#### 8.1. Criar um Script com Loop For
Crie um script chamado `count_lines.sh` que conta o número de linhas de todos os arquivos `.fasta` no diretório `bioinfo_exercicies`:

```bash
#!/bin/bash

for file in bioinfo_exercicies/*/*.fasta
do
  echo "Arquivo: $file"
  wc -l $file
done
```

Salve o script em `scripts/count_lines.sh`, dê permissão de execução e execute-o:

```bash
chmod +x scripts/count_lines.sh
./scripts/count_lines.sh
```

---

Este é o final do tutorial de comandos básicos do bash aplicados à genômica. Sinta-se à vontade para experimentar modificações e novos comandos!
