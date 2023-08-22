## Introducción a linux para bioinformática

**NOTA Puedes copiar cada bloque de código dando click en el botón derecho en cada recuadro**

### Conexión al servidor

```shell
ssh microbioXX@132.248.15.30 -p 7915 -o ServerAliveInterval=60

```

¿En dónde estamos y quiénes somos?

**`hostname`** Para saber en donde estamos conectados

```bash
hostname
```

**`whoami`**     Nombre del usuario con el que estamos conectados

**`pwd`**           Muestra la ruta absoluta en la que estamos posicionados

```bash
pwd
```

**`ls`**              Lista los contenidos de un directorio

```bash
ls
```

**NOTA: Cada comando tiene un manual de uso y regularmente tienen funciones extra.**

```shell
man ls
```



Recordemos como está estructurado nuestro sistema de ficheros.

<img src="https://github.com/DianaOaxaca/Introduccion_linux_para_bioinformatica/blob/main/Sistema_de_ficheros.jpg" alt="Sistema_de_ficheros" style="zoom:50%;" />



Puede constituirse por algunos de los siguientes directorios:

**`/`** - raiz del directorio virtual

**`/bin`** - directorio de binarios, donde se almacenan la mayor parte de los programas de GNU/Linux.

**`/etc`** - configuración del sistema de directorio de archivos.

**`/home`** - directorio home, donde Linux crea los directorios de usuarios.

**`/lib`** - directorio de librerías, donde se almacenan librerías del sistema y de aplicaciones.

> Antes de los sistemas gráficos, la única manera de interactuar con los sistemas Linux era a través de texto en una interfaz de linea de comandos (CLI) provista por el shell.
>



Veamos como está estructurado el sistema de ficheros del servidor al que estamos conectados

```bash
ls /
```



Existen varias maneras para referir al directorio home.

**`cd`**   El comando cd nos lleva directamente al directorio home

```bash
cd
```

**`$HOME`** La variable de entorno HOME contiene el nombre de nuestro directorio home

```bash
echo $HOME
```

El comando `echo` imprime el argumento de la variable `$HOME`
 **`~`** : Cuando se usa en lugar de directorio, la virgulilla es interpretada por el shell como el nombre del directorio **home**. 

```bash
echo ~
```



**`cd`** también nos ayuda a movernos de directorio, vamos a dirigirnos al directorio desde donde trabajaremos todas las prácticas

```bash
cd /botete/diana
```

Es importante distinguir entre `/home/Cyntia/`, `/Home/cyntia/`, `/home/cyntia/` , shell es sensible a mayúsculas y minúsculas.



Podemos crear directorios nuevos con **`mkdir`** y acceder a ellos

```bash
mkdir introduccion
cd introduccion
```

```bash
mkdir practica_uno
```

**NOTA**: Shell es sensible a espacios, es decir cada instrucción inicia y termina con un espacio, también es sensible a caracteres especiales como los acentos.

Podemos crear directorios dentro de directorios

```bash
mkdir -p practica_uno/subdir01
```

- [x] Entra al directorio `subdir01`



Con **`nano`** podemos crear archivos y escribir en ellos.

```bash
nano archivo_01.txt
```

```bash
Este es mi primer archivo
# Este es un comentario
Esta es la tercer línea
```

Dentro de nano hay varias funciones, las principales son:

**`ctrl`** + **`o`**  + **`enter`**  Guardar cambios

**`ctrl`** + **`c`**  + **`enter`**  Cancelar instrucción

**`ctrl`** + **`x`**  + **`enter`**  Cerrar el editor



Vamos a regresar al directorio `introduccion`

```bash
cd ../../
```

**Ruta relativa**: Inicia en el directorio actual

**Ruta absoluta**: Inicia desde la raíz **`/`**

```shell
. 		   #El directorio dónde estás parado
..       #El directorio arriba en la estructura de directorios
../../   #Dos directorios arriba en la estructura de directorios
~/       #Directorio HOME
```



¿Cómo está estructurado nuestro directorio `introduccion`?

**`tree`**     Nos muestra la estructura de los archivos del directorio en donde estamos 

```bash
tree
```



Ahora vamos a copiar `archivo1.txt` del directorio `subdir01` al directorio `practica_uno` 

Con **`cp`**   podemos copiar un archivo o directorio **`cp -r`** 

```bash
cp practica_uno/subdir01/archivo_01.txt practica_uno/
```



También podemos mover los archivos de ubicación en lugar de copiarlos con **`mv`**

```bash
mv practica_uno/archivo_01.txt .
```

OJO, `mv` también sirve para renombrar archivos y directorios

```bash
mv archivo_01.txt archivo_01_renombrado.txt
```

- [x] ¿Cómo se ve ahora la estructura de tu directorio  `introduccion`?
- [x] Regresa al directorio `subdir01` 
- [x] Mueve `archivo_01_renombrado.txt` a este directorio
- [x] Lista lo que contiene este directorio



Podemos observar el contenido de un archivo con **`cat`**

```bash
cat archivo_01_renombrado.txt
```

```bash
cat archivo_01.txt
```



Se trata del mismo archivo con nombres diferentes ¿cierto?. Borremos `archivo_01.txt`

```bash
rm archivo_01.txt
```

- [x] ¿Cómo se ve ahora la estructura de tu directorio  `introduccion`?



**Ejercicio 1**

> - [x] Crea el directorio `ejercicio_01` dentro del directorio `practica_uno`
> - [x] Posiciónate en tu directorio  `ejercicio_01`
> - [x]  Crea el directorio `primer-nivel`
> - [x] Dentro del directorio `primer-nivel` crea el directorio `segundo-nivel`
> - [x] Entra al directorio `segundo-nivel` y crea un archivo llamado `original.txt` y escribe tu nombre.
> - [x] Muévete a la carpeta  `ejercicio_01` usando rutas relativas.
> - [x] Copia el archivo `original.txt` usando rutas absolutas al directorio  `ejercicio_01`
> - [x] Renombra el archivo `original.txt` a `nombre.txt`
> - [x] Crea una copia del archivo `nombre.txt` dentro de la carpeta `primer-nivel`, esa copia debe
>   llamarse `primer-nivel.txt`
> - [x] Comprueba tu resultado listando la estructura del directorio `practica_uno`
> - [x] Elimina el archivo `nombre.txt`
> - [x] Elimina el directorio `segundo nivel`
> - [x] Imprime el contenido del directorio `practica_uno`
> - [x] ¿Cambió respecto a tu comprobación anterior?



```shell
## Algunos otros comandos ##
tail		 #Muestra las últimas lineas del contenido de un archivo
head		 #Muestra las primeras lineas del contenido de un archivo
which    #Muestra la ruta completa de un comando
locate   #Localizar archivos
history  #Muestra el historial de comandos
clear    #Limpia la pantalla
df       #Reporte de espacio en el disco duro
du       #Reporta la suma del tamaño de archivos
sort     #Ordena una serie de líneas
```

### Atajos en el teclado

**`TAB`**				                   	       Autocompletar comandos y nombres de archivos

**`Flechas arriba y abajo`**	   Navegar en la historia de comandos

**`Botón derecho del ratón`**	 Copiar y pegar texto

**`Ctrl+e`**										Ir al final de una línea

**`Ctrl+a`**                       				 Ir al inicio de una línea

**`Ctrl+k`**                         			   Borrar una línea

**`Ctrl+w`**                        				Elimina una palabra completa, del final al principio

**`Ctrl+c`**                         			   Abortar la ejecución del último comando

**`Ctrl+r+comando`**                	    Busca en el historial las lineas ejecutadas que contienen el comando  



### Descarga de datos

**Bases de datos**

Base de datos: Es una colección organizada de información estructurada, o datos, normalmente
almacenados electrónicamente en un sistema informático.
En bioinformática se utilizan diversas bases de datos, algunos ejemplos son:

NCBI: https://www.ncbi.nlm.nih.gov/

ENSEMBL: https://www.ensembl.org/index.html

UCSC Table Browser: https://genome.ucsc.edu/cgi-bin/hgTables

ENA: https://www.ebi.ac.uk/ena/browser/

Base de datos de bases de datos:
https://www.oxfordjournals.org/nar/database/cat/3

 

**Para amplicones:**

Trabajaremos con datos de amplicones de la región V3-V4 del 16S rRNA de muestras tres tiempos de fermentación del pulque, estos se obtuvieron con una plataforma ILLUMINA MiSeq (2 x 300 pb) y están en formato FASTQ. Los datos fueron depositados en NCBI y ENA bajo el BioProject **PRJEB13870** del artículo **[Deep microbial community profiling along the fermentation process of pulque, a biocultural resource of Mexico](https://www.sciencedirect.com/science/article/pii/S0944501320304614#sec0010)**. 

**FASTQ**: Normalmente se compone de cuatro lineas por secuencia:

```
@HWI-D00525:129:C6ACWANXX:5:1106:11467:38087
TGTCAAGACAGGCACGCACGTTCTGAATCAGCCGACGGTCGGTACGTAAGGCCATGTATATCGTGGCGTCCTTGTAAGTGATTTCCTTGCGTCCG
+
CCCCCGGGGGGGGGGGGGGGGGGGGGGGGGGGGGDGGFGGGGGGGGGGGGGGGGGGGGGGGGGGGGFGGGGGGGGGFGGGGGFGGGGGGEDGGGG
```

- L1 Comienza con '@' seguido del identificador de la secuencia y una descripción opcional
- L2 La secuencia de nucleótidos
- L3 Comienza con un '+' opcionalmente incluye el identificador de la secuencia
- L4 Indica los valores de calidad de la secuencia, debe contener el mismo número de símbolos que el número de nucleótidos.



Vamos a descargar el reporte del BioProject para obtener las ligas de descarga de cada librería, descarguemos el archivo tsv del reporte que se encuentra en la siguiente liga:

https://www.ebi.ac.uk/ena/browser/view/PRJNA556980

Ve a la terminal de tu computadora y sitúate en el directorio en donde se descargó el reporte.

```bash
cd ~/Downloads/
ls ~/Downloads/filereport_read_run_PRJNA556980_tsv.txt
```



El reporte que descargamos nos servirá para obtener los archivos **fastq** de cada librería secuenciada, pero necesitamos tenerlos en el servidor y no en nuestra máquina local. Así que vamos a subir el reporte al servidor.

Pero antes, vamos a crear el directorio en donde depositaremos el reporte y los fastq. 

En el servidor, crea los directorios `amplicones/data` dentro del directorio principal de trabajo y entra al directorio `data`

```bash
cd /botete/#USUARIO
mkdir -p amplicones/data
cd amplicones/data
```

Con **`scp`** podemos hacer copias de la computadora al servidor y visceversa.

Sitúate en la terminal de tu máquina local, justo en el directorio donde se encuentra el archivo que acabamos de descargar:

```bash
#Para subir archivos
scp -P 7915 filereport_read_run_PRJNA556980_tsv.txt [USUARIO]@132.248.15.30:/botete/[USUARIO]/amplicones/data

#Para descargar archivos
scp -P 7915 [USUARIO]@132.248.15.30:/botete/[USUARIO]/amplicones/data/[archivo] .
```

- [x] Ahora regresa a la terminal del servidor y lista el contenido del directorio `data`

Podemos ver que el reporte se aloja en este directorio. 

- [x] Cámbiale el nombre a `reporte.txt`

Con **`less`** podemos ver el contenido de este archivo

```bash
less -S reporte.txt
```

Algunas funciones del teclado dentro de **`less`**

> **q** 								   Salir del documento
>
> **Espacio o Enter**         Navegar hacia abajo
>
> **b o flecha arriba**       Navegar hacia arriba
>
> **/WORD**                         Búsqueda forward
>
> **?WORD**						 Búsqueda backward
>
> **N**									Anterior
>
> **G** 								   Ir al final del archivo
>
> **g**									 Ir al inicio del archivo
>
> **-S** 								  Mostrar una línea por renglón

Podemos notar que contiene la información de todas las librerías que se secuenciaron en el proyecto, sin embargo, a nosotros sólo nos interesan los que son de amplicones del 16S rRNA. Así que nos quedaremos sólo con esta información.

Con **`wc -l`** podemos conocer el número de líneas que contiene el archivo.

```bash
wc -l reporte.txt
```

¿Cuántas de estas corresponden a its?

 **grep** nos ayuda a buscar el patrón de texto en cada línea dentro del archivo.

```bash
grep --color 'its' reporte.txt
```

```bash
grep -c 'its' reporte.txt
```

```bash
grep -v 'its' reporte.txt
```

```bash
grep -c -v 'its' reporte.txt
```

La información que necesitamos para descargar los fastq son: el nombre de la muestra y la liga de descarga. Esta información se encuentra en las columnas `experiment_title` y `fastq_ftp` que son la tercer y sexta columna.

**`cut`** nos ayuda a obtener columnas de un archivo

```bash
cut -f3,6 reporte.txt
```

Para especificar el delimitador de las columnas usamos la bandera `-d`. 

Y para integrar una cadena de instrucciones podemos usar un pipe **`|`** entre cada instrucción. Ojo, la salida de cada instrucción, es la entrada de la siguiente instrucción.

```bash
cut -f3,6 reporte.txt| cut -d' ' -f4-7 | grep -v 'its'
```

Para guardar los resultados del filtrado de texto en un documento se puede utilizar **`>`** .

**`>`** Permite direccionar un resultado a un archivo nuevo. Crea el archivo si no existe y lo sobre escribe si existe.

Ahora si contiene sólo la información de las librerías del 16S, sin embargo aún nos falta un poco... Si recordamos, cada librería está pareada, si notamos el contenido de la columna 2 veremos que hay dos ligas de descarga separadas por un `;` así que necesitamos obtener cada liga por separado.

**`sed`** nos ayuda a sustituir patrones de texto o caracteres.

```bash
cut -f3,6 reporte.txt| cut -d' ' -f4-7 | grep -v 'its' | sed 's/;/\n\t/g' | grep -v 'experiment' > reporte_16S.txt
```

**`wget`** permite descargar archivos de la web al servidor o a la máquina local.

```bash
wget [liga al archivo de descarga]
```

Pero como son varios los archivos que necesitamos, haremos un *ciclo for* que nos ayude a optimizar esta tarea.

```bash
for fq in $(cut -f2 reporte_16S.txt); do wget $fq; done
```

Lista el contenido de tu directorio data, ¿qué contiene?

```bash
ls -lh
```

En los procesos de descarga, existe la posibilidad de que ocurra algún error de red que puede ocasionar la descarga fallida de los archivos.

**`md5sum`** ayuda a verificar la integridad mediante la impresión de un identificador único de cada archivo.

Obtengamos el identificador md5 desde el reporte de los datos

```bash
cut -f3,5 reporte.txt | cut -d' ' -f4-7 | grep -v 'its' | sed 's/;/\n\t/g' | grep -v 'experiment' | cut -f2
```

Ahora generemos el identificador de los datos que ya descargamos

```bash
md5sum SRR9849602_1.fastq.gz
```

Pero otra vez son muchos, hagamos un ciclo for para esto:

```bash
for gz in $(ls *.gz); do md5sum $gz ; done
```

Podemos verlo con **`zless`** 

```bash
zless SRR9849602_1.fastq.gz
```

**Listo!!!** tenemos los datos para el análisis de amplicones.



### Ejercicio extra, descargar un genoma

* Link para genomas de referencia NCBI: https://ftp.ncbi.nlm.nih.gov/genomes/refseq/

* Link para el genoma de Raoultella terrigena: https://ftp.ncbi.nlm.nih.gov/genomes/refseq/bacteria/Raoultella_terrigena/representative/GCF_012029655.1_ASM1202965v1/

Primero vamos a crear nuestro espacio de trabajo

```shell
mkdir Intro
cd Intro
mkdir data results && cd data
```

**`&&`** permite dar dos instrucciones seguidas sin depender del resultado de la primer instrucción.


* Descarga el genoma representativo de Raoultella terrigena de la Refseq de NCBI

```bash
wget -O Raoultella_terrigena.fasta.gz https://ftp.ncbi.nlm.nih.gov/genomes/refseq/bacteria/Raoultella_terrigena/representative/GCF_012029655.1_ASM1202965v1/GCF_012029655.1_ASM1202965v1_genomic.fna.gz
#El flag es letra O mayúscula
#Para mobaxterm
wget --no-check-certificate

```

* Descargar el archivo de aminoacidos

```shell
curl https://ftp.ncbi.nlm.nih.gov/genomes/refseq/bacteria/Raoultella_terrigena/representative/GCF_012029655.1_ASM1202965v1/GCF_012029655.1_ASM1202965v1_protein.faa.gz > Raoultella_terrigena.faa.gz
```

**`>`** Permite direccionar un resultado a un archivo nuevo. Crea el archivo si no existe y lo sobre escribe si existe

* Descarga el archivo de anotación

```shell
wget -O Raoultella_terrigena.gff.gz https://ftp.ncbi.nlm.nih.gov/genomes/refseq/bacteria/Raoultella_terrigena/representative/GCF_012029655.1_ASM1202965v1/GCF_012029655.1_ASM1202965v1_genomic.gff.gz
```

* Ahora descarga el archivo md5checksums.txt del directorio genomes/refseq/bacteria/Raoultella terigena de NCBI

```shell
curl https://ftp.ncbi.nlm.nih.gov/genomes/refseq/bacteria/Raoultella_terrigena/representative/GCF_012029655.1_ASM1202965v1/md5checksums.txt > md5sum_R.terrigena.txt
```

* Regresa al directorio de trabajo

```shell
cd ../
```

* Revisemos la integridad de los archivos

```sh
shasum data/Raoultella_terrigena.fasta.gz
md5sum data/Raoultella_terrigena.fasta.gz
more data/md5sum_R.terrigena.txt
```

Pero si son muchos?

```shell
## 
for gz in $(ls data/*.gz); do md5sum $gz ; done | cut -d ' ' -f1 >> results/md5sum_Rt.txt
```

**`>>`** Permite redireccionar un resultado en pantalla o un archivo a otro, sin remplazar o
sobreescribir. Crea el archivo si no existe y agrega el nuevo contenido al final, si el archivo
existe.

##### También podríamos descargar todos los archivos de un BioProject de NCBI 

```shell
#fastq-dump --split-files SRR1234567
```

##### Ahora descargaremos y transferiremos un archivo al servidor

* Dirigete a la siguiente liga: https://fungi.ensembl.org/index.html

`scp` Security Copy Shell

``` shell
`scp` [FUENTE][DESTINO]
#FUENTE=Nombre del archivo que quieres transferir
#DESTINO=Ruta de destino
#Ejemplo de mi computadora al servidor:
scp Puccinia_graminis.ASM14992v1.53.gff3.gz dhernandez@132.248.248.175:/home/dhernandez/Intro/data/
#Me pedirá el password
#Funciona de manera inversa si quieres bajar del servidor a tu computadora
scp dhernandez@132.248.248.175:/home/dhernandez/Intro/data/Puccinia_graminis.ASM14992v1.53.gff3.gz .#ojo el
destino puede ser con ruta absoluta o relativa, aquí fue relativa "."
#También puedes usar rsync
`rsync -e ssh` [FUENTE][DESTINO]
# -e ssh indica que nos conectaremos al servidor a través de una conexión de
tipo ssh
```

* Para descomprimir archivos usamos `gunzip`

```shell
#Podemos correr esta linea indicando archivo por archivo
gunzip data/Raoultella_terrigena.faa.gz
#O podemos usar un comodin
gunzip data/*.gz
```

* Podemos ver el archivo con `less`

```shell
less data/Raoultella_terrigena.gff 
```

#### Búsquedas y conteos

`sort` Ordena una serie de líneas

`cut` Corta una sección de cada línea

`uniq` Filtra lineas repetidas

`wc` Cuenta líneas, carácteres y bytes

 `grep` permite buscar patrones, algunas opciones que tiene:

**`--colour`** Marca el texto que corresponde al patrón

**`-E`** Interpreta el patrón como una expresión regular

**`-P`** Interpreta el patrón como una expresión regular extendida, tipo Perl

**`-f`** Lee uno o más patrones a partir de un archivo

**`-i`** Ignora mayúsculas/minúsculas

**`-n`** Imprime el número de línea donde se encontró el patrón -

**`-v`** Selecciona las líneas en donde no ocurre el patrón

**`-w`** Realiza una búsqueda estricta

La diferencia con **`&&`** es que **`|`** requiere la salida de una instrucción como entrada de la otra y `&&` ejecuta instrucciones independientes.

* ¿Cuántos cromosomas tiene *Raoultella terrigena*?

```shell
cut -f1 data/Raoultella_terrigena.gff | sort | uniq -c
#Eliminar encabezado
grep -v "#" data/Raoultella_terrigena.gff | cut -f1 | sort| uniq
```

* ¿En cuáles tipos de features se clasifica el genoma de *R. terrigena*?

```shell
cut -f3 data/Raoultella_terrigena.gff | sort -u
```

* ¿Cuáles son las fuentes de los datos de anotación?

```shell
cut -f2 data/Raoultella_terrigena.gff | sort -u
```

* ¿Cuántos genes y cuántos CDS tiene el genoma de R.terrigena?

```shell
cut -f3 data/Raoultella_terrigena.gff | sort | uniq -c
##
cut -f3-5 data/Raoultella_terrigena.gff | sort -u | cut -f1 | sort | uniq -c
```

* Escribe un archivo de anotación que esté ordenado por cadena y por región genómica

```shell
sort -k7,7 -k4,4n data/Raoultella_terrigena.gff | less -s
sort -k7,7 -k4,4n data/Raoultella_terrigena.gff > results/R.terrigena_strand.gff
```

* ¿Cuántos genes con diferente nombre existen en el genoma de R. terrigena?

```shell
grep "gene" data/Raoultella_terrigena.gff
grep "gene" data/Raoultella_terrigena.gff | cut -f3 | sort -u
grep -P "\tgene" data/Raoultella_terrigena.gff | cut -f3 | sort -u


### Ahora si, paso por paso
## Obtener únicamente los genes
grep -P "\tgene" data/Raoultella_terrigena.gff | head
## Acceder a la columna 9
grep -P "\tgene" data/Raoultella_terrigena.gff | cut -f9 | head
## Separar esa info por ;
## Quedarnos con la columna 3
grep -P "\tgene" data/Raoultella_terrigena.gff | cut -f9 | cut -d ';' -f3 | head
## Obtener los valores únicos
grep -P "\tgene" data/Raoultella_terrigena.gff | cut -f9 | cut -d ';' -f3 | sort -u | head
## Contar el número de valores únicos
grep -P "\tgene" data/Raoultella_terrigena.gff | cut -f9 | cut -d ';' -f3 | sort -u | wc -l
```

* ¿Cuántos genes (ID distinto) existen en el genoma de R. terrigena?

```shell
grep -P "\tgene" data/Raoultella_terrigena.gff | cut -f9 |cut -d ';' -f1 | grep "ID=gene-" | sort -u | wc -l
```

* ¿Cuál es la longitud de la secuencia de la proteína WP_000448832.1?
  ¿Cuál es el algoritmo?
  Extraer la ubicación del ID WP_000448832.1
  Obtener el siguiente ID
  conocer el número de lineas de WP_000448832.1
  Extraer la secuencia del ID WP_000448832.1
  Obtener el número de caractéres de la secuencia

```shell
grep ">" data/Raoultella_terrigena.faa | grep -n "WP_000448832.1"
grep ">" data/Raoultella_terrigena.faa | head -7
grep -n "WP_000448832.1" data/Raoultella_terrigena.faa
grep -n "WP_000487600.1" data/Raoultella_terrigena.faa
head -18 data/Raoultella_terrigena.faa | tail -2
head -18 data/Raoultella_terrigena.faa | tail -2 | wc
###Listo
112 bytes
2 lineas, 1 byte por salto de linea = 111 caraceteres de secuencia
```

* ¿Cuál es el protein_id del gene fnr?

```shell
grep --color "fnr" data/Raoultella_terrigena.gff
### agreguémos más contexto
grep --color ";gene=fnr" data/Raoultella_terrigena.gff | grep --color "protein_id"
```

* Extrae y guarda en un archivo fasta la secuencia de la proteina fnr de Raoultella terrigena

```shell
grep '>' data/Raoultella_terrigena.faa | head -29 | tail -2
grep '>' data/Raoultella_terrigena.faa | grep -n WP_002903394.1
grep -n WP_002903394.1 data/Raoultella_terrigena.faa
grep -n WP_002913148.1 data/Raoultella_terrigena.faa
head -79 data/Raoultella_terrigena.faa | tail -5 > results/FNR.faa
```

* Pero podemos extraer un montón de secuencias de una forma más sencilla

```shell
grep 'Nif' data/Raoultella_terrigena.faa | sed 's/>//g' > results/nif_headers.txt
seqtk subseq data/Raoultella_terrigena.faa results/nif_headers.txt > results/nif.faa
less results/nif.faa 
```

