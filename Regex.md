## Expressões regulares: introdução

Uma expressão regular é uma notação para representar padrões em strings. Serve para validar entradas de dados ou fazer busca e extração de informações em textos.

Por exemplo, para verificar se um dado fornecido é um número de 0,00 a 9,99 pode-se usar a expressão regular \d,\d\d, pois o símbolo \d é um curinga que casa com um dígito.

O verbo casar aqui está sendo usado tradução para match, no sentido de combinar, encaixar, parear. Dizemos que a expressão \d,\d\d casa com 1,23 mas não casa com 123 (falta a vírgula) nem com 1,2c (“c” não casa com \d, porque não é um dígito).

O termo em inglês é regular expression de onde vem as abreviações regex e re.

### Algums exemplos
Veja alguns exemplos com breves explicações para ter uma idéia geral:

##### \d{5}-\d{3}

O padrão de um CEP como 05432-001: 5 dígitos, um - (hífen) e mais 3 dígitos. A sequência \d é um metacaractere, um curinga que casa com um dígito (0 a 9). A sequência {5} é um quantificador: indica que o padrão precedente deve ser repetido 5 vezes, portanto \d{5} é o mesmo que \d\d\d\d\d.

##### [012]\d:[0-5]\d

Semelhante ao formato de horas e minutos, como 03:10 ou 23:59. A sequência entre colchetes [012] define um conjunto. Neste caso, o conjunto especifica que primeiro caractere deve ser 0, 1 ou 2. Dentro dos [] o hífen indica uma faixa de caracteres, ou seja, [0-5] é uma forma abreviada para o conjunto [012345]; o conjunto que representa todos os dígitos, [0-9] é o mesmo que \d. Note que esta expressão regular também aceita o texto 29:00 que não é uma hora válida (horas válidas serão o tema de um dos Exercícios).

##### [A-Z]{3}-\d{4}

É o padrão de uma placa de automóvel no Brasil: três letras de A a Z é seguidas de um - (hífen) seguido de quatro dígitos, como CKD-4592.

