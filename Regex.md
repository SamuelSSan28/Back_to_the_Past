## Expressões regulares: introdução

Uma expressão regular é uma notação para representar padrões em strings. Serve para validar entradas de dados ou fazer busca e extração de informações em textos.

Por exemplo, para verificar se um dado fornecido é um número de 0,00 a 9,99 pode-se usar a expressão regular \d,\d\d, pois o símbolo \d é um curinga que casa com um dígito.

O verbo casar aqui está sendo usado tradução para match, no sentido de combinar, encaixar, parear. Dizemos que a expressão \d,\d\d casa com 1,23 mas não casa com 123 (falta a vírgula) nem com 1,2c (“c” não casa com \d, porque não é um dígito).

O termo em inglês é regular expression de onde vem as abreviações regex e re.

### Algums exemplos
Veja alguns exemplos com breves explicações para ter uma idéia geral:

#### \d{5}-\d{3}

  O padrão de um CEP como 05432-001: 5 dígitos, um - (hífen) e mais 3 dígitos. A sequência \d é um metacaractere, um curinga que casa com um dígito (0 a 9). A sequência {5} é um     quantificador: indica que o padrão precedente deve ser repetido 5 vezes, portanto \d{5} é o mesmo que \d\d\d\d\d.

#### [012]\d:[0-5]\d

  Semelhante ao formato de horas e minutos, como 03:10 ou 23:59. A sequência entre colchetes [012] define um conjunto. Neste caso, o conjunto especifica que primeiro caractere       deve ser 0, 1 ou 2. Dentro dos [] o hífen indica uma faixa de caracteres, ou seja, [0-5] é uma forma abreviada para o conjunto [012345]; o conjunto que representa todos os         dígitos, [0-9] é o mesmo que \d. Note que esta expressão regular também aceita o texto 29:00 que não é uma hora válida (horas válidas serão o tema de um dos Exercícios).

#### [A-Z]{3}-\d{4}

  É o padrão de uma placa de automóvel no Brasil: três letras de A a Z é seguidas de um - (hífen) seguido de quatro dígitos, como CKD-4592.

### Metacaracteres
Um metacaractere é um caractere ou sequência de caracteres com significado especial em expressões regulares. Os metacaracteres podem ser categorizados conforme seu uso.

### Especificadores
Especificam o conjunto de caracteres a casar em uma posição.

| metacaractere  |  conhecido como | significado  |
|---|---|---|
.	|curinga	|qualquer caractere, exceto a quebra de linha \n |
[...]	| conjunto|	qualquer caractere incluido no conjunto |
[^...]	|conjunto negado|	qualquer caractere não incluido no conjunto|
\d	|dígito	o mesmo que [0-9]|
\D	|não-digíto|	o mesmo que [^0-9]|
\s	|branco	espaço, quebra de linha, tabs etc.;| o mesmo que [ \t\n\r\f\v]|
\S	|não-branco|	o mesmo que [^ \t\n\r\f\v]
\w	|alfanumérico|	o mesmo que [a-zA-Z0-9_] (mas pode incluir caracteres Unicode; ver flag_unicode)|
\W	|não-alfanumérico|	o complemento de \w|
\	|escape	|anula o significado especial do metacaractere seguinte; por exemplo, \. representa apenas um ponto, e não o curinga|

### Quantificadores
Definem o número permitido repetições da expressão regular precedente.

| metacaractere  | significado  |
|---|---|
{n}	|exatamente n ocorrências|
{n,m}	|no mínimo n ocorrências e no máximo m|
{n,}	|no mínimo n ocorrências|
{,n}	|no máximo n ocorrências|
|?	|0 ou 1 ocorrência; o mesmo que {,1}|
|+	|1 ou mais ocorrência; o mesmo que {1,}|
|*	|0 ou mais ocorrência|
|«q»?	|modera qualquer um dos quantificadores acima |


### Gula × moderação
Por default, todos os quantificadores são gulosos: tentam casar a maior quantidade possível de caracteres.

Para entender o que isso significa, considere que desejamos capturar o nome do primeiro tag (h1) no fragmento de HTML abaixo:

    html = '<h1>Alan Turing: 100 anos</h1>'

Usando o quantificador guloso +, acabamos por capturar o elemento inteiro, e não apenas o tag:

    res = re.match('<.+>', html)
    res.group()
    '<h1>Alan Turing: 100 anos</h1>'

O resultado acima ocorre porque o sinal > casa em duas posições no texto, e casando na segunda posição o curinga guloso .+ captura mais caracteres.

Se usamos o quantificador moderado +?, a expressão .+? fica satisfeita em capturar apenas os caracteres até o primeiro casamento de >:

    res = re.match('<.+?>', html)
    res.group()
    '<h1>'
    
### Exercises:

#### Exercise 1: Matching Characters

 - Match:	abcdefg	To be completed
 - Match;	abcde	To be completed
 - Match:	abc

 - Solution: [\w]{1,} 

#### Exercise 2: Matching Digits
  
 - Match:	cat.	 
 - Match	896.	 
 - Match	?=+.	   
 - Skip	abc1;

 - Solution:  ...\.
 

#### Exercise 2: Matching Any Character
  
 - Match:	abc123xyz
 - Match:	define "123"	
 - Match:	var g = 123;

 - Solution:  [\d]{1,3}, [^\D]{1,3} 
  
  
#### Exercise 4: Matching Only a, b, or c

 - Match:	can	
 - Match:	man	
 - Match:	fan
 - Skip	dan	
 - Skip	ran	
 - Skip	pan

 - Solution: 
      - You can use the expression [cmf]an] to match only 'can', 'man' and 'fan' without matching any other line. 
      - You can also use the inverse expression [^drp]an] to match any three letter word ending with 'an' that does not start with 'd', 'r' or 'p'.} 
  
  
#### Exercise 4: Only the live animals (hog, dog, but not bog).

 - Match	hog	
 - Match	dog	
 - Skip	bog

 - Solution: [^b]og
  
  
#### Exercise 5: Matching Character Ranges

 - Match:	Ana	
 - Match:	Bob	
 - Match:	Cpc	
 - Skip:	aax	
 - Skip:	bby	
 - Skip:  ccz
 - Solution: [A-Z][a-z]{1,}


#### Exercise 6: Matching Repeated Characters

 - Match	wazzzzzup	
 - Match	wazzzup	
 - Skip	wazup
 
 - Solution: z{2,5}


#### Exercise 7: Matching Repeated Characters

 - Match	wazzzzzup	
 - Match	wazzzup	
 - Skip	wazup
 
 - Solution: z{2,5}


#### Exercise 7: Matching Repeated Characters pt2

 - Match: aaabcc	
 - Match:	aabbbbc	
 - Match:	aacc	
 - Skip: a
 
 - Solution: a{2,4b{0,4}{1,2} , aa+b*c+


#### Exercise 8: Matching Optional Characters

 - Match:	1 file found?	
 - Match:	2 files found?	
 - Match:	24 files found?	
 - Skip:	No files found.
 
 - Solution: \d+ files? found\?
  
  
#### Exercise 9: Matching Whitespaces

 - Match:	1.   abc
 - Match:	2.	abc	
 - Match:	3.           abc	
 - Skip:	4.abc
 
 - Solution: \d.\s+\w+


#### Exercise 10: Matching Lines

 - Match	Mission: successful	
 - Skip	Last Mission: unsuccessful	
 - Skip	Next Mission: successful upon capture of target
 
 - Solution: ^Mission: successful$

  
#### Exercise 11: Matching Groups

 - Capture:	file_record_transcript.pdf	(file_record_transcript)
 - Capture	file_07241999.pdf	(file_07241999)	
 - Skip	testfile_fake.pdf.tmp

 - Solution: ^(file\w+)\.pdf$


#### Exercise 11: Matching Groups

 - Capture:	file_record_transcript.pdf	(file_record_transcript)
 - Capture:	file_07241999.pdf	(file_07241999)	
 - Skip:	testfile_fake.pdf.tmp
 - Solution: ^(file\w+)\.pdf$


#### Exercise 12: Matching Nested Groups

 - Capture:	Jan 1987	(Jan 1987) (1987)	 
 - Capture:	May 1969	(May 1969) (1969)	 
 - Capture:	Aug 2011	(Aug 2011) (2011)
 - Solution: ^(\w{1,3} (\d+))$


#### Exercise 13: Matching Nested Groups

 - Capture:	1280x720	(1280) (720)
 - Capture:	1920x1600	(1920) (1600)
 - Capture:	1024x768	(1024) (768)
 - Solution: ^(\w{1,3} (\d+))$


#### Exercise 13: Matching Nested Groups

 - Capture:	1280x720	(1280) (720)
 - Capture:	1920x1600	(1920) (1600)
 - Capture:	1024x768	(1024) (768)
 - Solution: ^(\w{1,3} (\d+))$


#### Exercise 14: Matching Conditional Text

 - Match:	I love cats	
 - Match:	I love dogs	
 - Skip:	I love logs
 - Skip:	I love cogs
 - Solution: I love (cats|dogs)


#### Exercise 14: Matching Conditional Text

 - Match:	I love cats	
 - Match:	I love dogs	
 - Skip:	I love logs
 - Skip:	I love cogs
 - Solution: I love (cats|dogs)


### Lesson X: Infinity and beyond!
