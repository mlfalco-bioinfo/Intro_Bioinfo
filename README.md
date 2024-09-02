# Tutorial de Comandos Básicos do Bash Aplicados à Genômica

<p align="justify">
Este tutorial tem como objetivo ensinar comandos básicos do bash aplicados em um contexto de bioinformática, utilizando uma estrutura de diretórios e arquivos relacionados à genômica.
O minicurso pertence a <a href="https://www.instagram.com/sebiounicentro?igsh=MWI4ODc4djE2Nm9sZA==">XXVIII SEBIO<a/> (Semana da Biologia) na Universidade Estadual do Centro Oeste <a href="https://www3.unicentro.br/">(Unicentro/PR)</a>.
</p>

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

```
echo "Bem-vindo ao tutorial de bash aplicado à bioinformática"
```

#### 1.2. Mostrar o Diretório Atual
O comando `pwd` mostra o caminho do diretório atual:

```
pwd
```

#### 1.3. Navegar Entre Diretórios
Use o comando `cd` para navegar para o diretório `bioinfo_exercicies/dna`:

```
cd bioinfo_exercicies/dna
```

Use `cd ..` para voltar ao diretório pai (`bioinfo_exercicies`):

```
cd ..
```

### 2. Listagem de Arquivos

#### 2.1. Listar o Conteúdo de um Diretório
Liste o conteúdo do diretório `bioinfo_exercicies` usando o comando `ls`:

```
ls bioinfo_exercicies
```

Liste o conteúdo com detalhes, incluindo arquivos ocultos e tamanhos legíveis:

```
ls -lah bioinfo_exercicies
```

### 3. Download de Arquivos

#### 3.1. Baixar um Arquivo Usando `wget`

Baixe o arquivo com nossos arquivos e diretórios:

```
wget -P $HOME https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.12.1.zip
```
Agora, é necessário descomprimir o arquivo `Intro_Bionfo.zip` com os diretórios/arquivos:

```
unzip Intro_Bioinfo.zip .
```


### 4. Estrutura de Diretórios

#### 4.1. Visualizar a Estrutura de Diretórios
Use o comando `tree` para visualizar a estrutura de diretórios:

```
tree bioinfo_exercicies
```

#### 4.2. Criar um Novo Diretório
Crie um diretório chamado `genoma`:

```
mkdir genoma
```

### 5. Manipulação de Arquivos

#### 5.1. Copiar Arquivos
Copie o arquivo `chromossome.txt` para o diretório `chrom`:

```
cp bioinfo_exercicies/chromossome.txt chrom/
```

#### 5.2. Mover Arquivos
Movimente o arquivo `genes.vcf` para o diretório `genoma`:

```
mv genes.vcf genoma/
```

#### 5.3. Remover Arquivos
Remova o arquivo `genoma/genes.vcf`:

```
rm genoma/genes.vcf
```

### 6. Visualização de Conteúdo de Arquivos

#### 6.1. Exibir as Primeiras e Últimas Linhas de um Arquivo
Exiba as primeiras 10 linhas do arquivo `dna.fasta`:

```
head bioinfo_exercicies/dna/dna.fasta
```

Exiba as últimas 10 linhas do arquivo `protein.fasta`:

```
tail bioinfo_exercicies/protein/protein.fasta
```

#### 6.2. Concatenar e Exibir Conteúdo de Arquivos
Use `cat` para exibir o conteúdo do arquivo `rna.fasta`:

```
cat bioinfo_exercicies/rna/rna.fasta
```

#### 6.3. Criar um Arquivo Vazio
Use `touch` para criar um novo arquivo chamado `genome.txt` no diretório `genoma`:

```
touch genoma/genome.txt
```

### 7. Uso de `grep`, `pipe` e `nano`

#### 7.1. Procurar Padrões em Arquivos com `grep` e Usar `pipe`
Use o comando `grep` para procurar pela sequência "ATGC" no arquivo `dna.fasta`:

```
grep "ATGC" bioinfo_exercicies/dna/dna.fasta
```

Combine o comando `grep` com `pipe` (`|`) para contar o número de ocorrências da sequência "ATGC":

```
grep "ATGC" bioinfo_exercicies/dna/dna.fasta | wc -l
```

**EASTER EGGS**

Utilize o comando `grep`com a palavra "LINUX" pesquisando o arquivo `rna.fasta`

#### 7.2. Editar Arquivos Usando `nano`
Abra o arquivo `first.sh` no editor de texto `nano`:

```
nano scripts/first.sh
```

### 8. Usando [FASTQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)

#### 8.1. Download

```
wget -P $HOME/Intro_Bioinfo/fastq/ https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.12.1.zip
```

#### 8.2 Verificação JAVA

```
java - version
```

#### 8.3 Instalação

Alterando permissão do arquivo `fastqc`:

```
chmod 755 fastqc
```

Comando ára rodar o programa:
```
./fastqc
```

Ou criação de um link simbólico para rodar de qualquer local no sistema:

```
sudo ln -s /path/to/FastQC/fastqc /usr/local/bin/fastqc
```

### 9. Usando FASTQC

#### 9.1. Principal Comando

Primeiro criar um diretório para envia os resultados do fastqc:

```
mkdir results
```

Para usar o programa `fastqc` siga a linha abaixo, precisa alterar a palavra ARQUIVO
por um arquivo de sua escolha, dentro do diretório `fastq`:

```
fastqc -f fastq -t 4 -o results ARQUIVO
```

### 10. Criação de Scripts

#### 10.1. Criar um Script com For loop
Crie um script chamado `count_lines.sh` que conta o número de linhas de todos os arquivos `.fasta` no diretório `bioinfo_exercicies`:

```
#!/bin/bash

for file in bioinfo_exercicies/*/*.fasta
do
  echo "Arquivo: $file"
  wc -l $file
done
```

Salve o script em `scripts/count_lines.sh`, dê permissão de execução e execute-o:

```chmod +x scripts/count_lines.sh
./scripts/count_lines.sh
```
### 11. Criação de Script FASTQC

#### 11.1. Reprodutibilidade - Rodando vários arquivos.

Nesse exercício, crie um script com uma sequência em *for loop* para rodar todos os arquivos .fastq dentro do diretório `fastq`:

```
?
```

---

Este é o final do tutorial de comandos básicos do bash aplicados à genômica. Sinta-se à vontade para experimentar modificações e novos comandos!

---

Este tutorial é mantido pelo [AUTHOR](https://github.com/mlfalco-bioinfo/Intro_Bioinfo/blob/main/AUTHOR). Se desejar utlizar o material siga as intruções do CODE OF CONDUCT.
