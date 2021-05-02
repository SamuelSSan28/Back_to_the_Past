## # 26/04/202 a 01/05/2021

### **SPA - Single Page Aplication**

São aplicações cuja funcionalidade está concentrada em uma única página. Ao invés de recarregar toda a página ou redirecionar o usuário para uma página nova, apenas o conteúdo principal é atualizado de forma assíncrona, mantendo toda a estrutura da página estática.

Imagine um dashboard, em que os menus lateral e superior são os mesmos para todas as telas da aplicação. Ao clicar em uma opção como “Cadastro de produtos”, o usuário não precisaria recarregar toda a página para ver que no fim apenas o conteúdo central mudou. Para evitar isso, mantemos os menus fixos e alteramos apenas a parte do meio, em que estarão os formulários, tabelas, etc.

Além de otimizar a performance da aplicação, reduzindo o conteúdo a ser carregado, as SPAs têm foco na experiência do usuário, que lida com uma interface mais rápida.

### Server-side-render (Ex: NEXT.JS)

Server Side Rendering ou SSR é o processo de pegar todos os Javascript e todos os CSS de um site que, geralmente é carregado no browser (client-side), e renderizá-los como estático do lado do servidor.

Com isso podemos obter um site com um tempo de carregamento reduzido e totalmente indexável por SEO’s. Mas para entender um pouco desse tempo de carregamento, temos que entender os princípios do carregamento que é realizado no seu browser para ver o real benefício de se usar algum framework SSR.

SEO (Search Engine Optimization) é um conjunto de técnicas que visa posicionar uma página nos primeiros resultados de mecanismos de busca online, como o Google.

Quando acessamos um conteúdo na web, temos uma referência no documento HTML que nos indica o que será carregado e também será a primeira coisa que o browser vai receber, esse documento contém todas as referências necessárias para os seguintes assets, como imagens, CSS e javascripts.

O browser sabe que a partir disso ele precisa ir a algum lugar para localizar e baixar esses assets, enquanto ele vai construindo o documento. Então, mesmo que o browser contenha toda a estrutura HTML, ele não poderá renderizar algo amigável até que o CSS correspondente, que contém toda a sua estilização, seja também carregado.

Os arquivos poderão ser grandes e com o uso de uma internet ruim o tempo de carregamento poderá ser grande. Desta maneira, a experiência do seu usuário não será a ideal, o que pode piorar se a primeira renderização depender de algum arquivo javascript.

O grande diferencial de usar SSR é que podemos entregar, quase que imediatamente, um conteúdo significante para o usuário.. Isto acontece porque o HTML e seus principais assets são carregados em um mesmo arquivo e entregue ao client.

### Static site generators (SSG)

A maior diferença entre um gerador de site estático e uma  aplicatição web tradicional é que, em vez de esperar até que uma página seja solicitada e, em seguida, gerar sua visualização sob demanda a cada vez, um gerador de site estático faz isso com antecedência para que a visualização esteja pronta para servir antes do tempo. E faz isso para todas as visualizações possíveis de um site no momento da construção.

Por que usar um **static site generator** ?

Segurança 

Como os geradores de sites estáticos criam um conjunto de ativos estáticos que podem ser servidos a partir de um servidor web simplificado, ou melhor ainda - direta e completamente de uma rede de distribuição de conteúdo (CDN), eles têm um perfil de segurança notavelmente bom. 

Como eles são renderizados com antecedência e prontos para servir, a infraestrutura envolvida em atendê-los pode ser extremamente simplificada e ter poucos vetores para ataques mal-intencionados. Quando removemos a necessidade de os servidores executarem lógica e trabalho, removemos maneiras de os agentes mal-intencionados injetarem códigos maliciosos e enganá-los para que executem ações nefastas.

E quando não precisamos acessar bancos de dados, realizar operações lógicas ou modificar recursos para cada visualização, podemos simplificar drasticamente nossa infraestrutura de hospedagem. Isso também melhora a segurança, pois há menos servidores fisicamente envolvidos no tratamento de solicitações.

> There is no server more secure than the one that does not exist.

Escalabilidade 

Cada página está pronta para ser veiculada sem trabalho de servidor adicional a cada solicitação. Não precisamos adicionar mais capacidade de computação para lidar com picos de tráfego porque não estamos compilando uma resposta para cada solicitação sob demanda. Nós fizemos o trabalho antes. 

Conseguimos garantir que tudo estava correto, como parte de nosso processo de construção automatizado, e agora simplesmente fornecemos aos usuários o que eles pediram.

Isso se assemelha ao tipo de cache que as arquiteturas tradicionais costumam adicionar como uma camada além da infraestrutura dinâmica subjacente. Mas nos permite renunciar ao gerenciamento complexo do que é armazenado em cache e do que precisa ser atualizado com base em muitos parâmetros diferentes. Com um site pré-construído, tudo pode ser armazenado em cache no CDN e servido diretamente. A arquitetura é otimizada para escala por padrão.

Desempenho

O tempo que leva para uma solicitação ser atendida é impactado pela distância que ela deve percorrer, o número de sistemas com os quais deve interagir e o trabalho que está sendo feito em cada um desses sistemas.

Quando criamos nossos sites com um gerador estático de sites, os visitantes não precisam interagir com nenhuma das máquinas envolvidas na geração de cada visualização! Podemos entregar o resultado de todo esse trabalho anterior diretamente de uma rede distribuída de caches (um CDN), diminuindo a distância que as solicitações percorrem e evitando totalmente a interação com qualquer um dos sistemas.

O desempenho pode disparar. E as dores de cabeça de planejamento e orçamento para a infraestrutura necessária para manter esse desempenho durante os níveis de tráfego planejados (e não planejados!) Vão embora.

### Ferramentas de Transpilação

O ES6 não era suportado pela maioria dos navegadores da Web, portanto, os desenvolvedores se depararam com problemas de compatibilidade do navegador.

Conheça agora duas ferramentas importantes para resolver problemas de compatibilidade do navegador:

- caniuse.com — Um site que fornece dados sobre compatibilidade com navegadores para recursos HTML, CSS e JavaScript. Você aprenderá como usá-lo para procurar o recurso de suporte do ES6.
- Babel — O babel é um conjunto de ferramentas, utilizado principalmente para converter o código ECMAScript 2015+ em uma versão compatível com versões anteriores do JavaScript em navegadores ou ambientes antigos.

Desde o lançamento do ECMAScript2015 (ES6) pela Ecma, as empresas de software adicionaram lentamente suporte para os recursos e a sintaxe do ES6. Para a nossa tranquilidade, a maioria das novas versões de navegadores já suportam a maioria das bibliotecas do ES6, porém ainda existem alguns problemas de compatibilidade no que diz respeito a:

- Alguns usuários não atualizaram para a versão mais recente do navegador da Web suportada pelo ES6.
- Alguns recursos do ES6, como “módulos” por exemplo, ainda não são suportados por certos navegadores da web.

Anteriormente, convertemos o código ES6 manualmente para ES5. Embora a conversão manual demore apenas alguns minutos, é insustentável à medida que o tamanho do arquivo JavaScript aumenta. Como o ES6 é consequentemente compatível com versões anteriores, um grupo de programadores JavaScript desenvolveu uma biblioteca JavaScript chamada **Babel** que *transpila o* ES6 JavaScript para o ES5.

***Transpilação** é o processo de conversão de uma linguagem de programação para uma outra linguagem, ou a mesma escrita de outra forma.*

No fundo a transpilação é uma especialização da compilação. Todo o processo é feito igualzinho o que o compilador faz, a diferença é apenas que no compilador tradicional o alvo é um código de mais baixo nível, provavelmente alguma forma de Assembly ou código de máquina, enquanto que o transpilador tem como alvo um código fonte de uma linguagem de alto nível diferente ou a mesma escrita de outra forma.

**Webpack**

O webpack é um empacotador de módulos estáticos para aplicações JavaScript modernas. Ao processar a aplicação o webpack gera um gráfico que mapeia cada módulo e suas dependências e gera um ou mais pacotes. É reponsável pela build de projetos utilizando framworks como React, Next, Vue e etc.
