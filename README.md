# Starter Kit v4 - Eleventy Blog + Netlify CMS

## Índice

- [Visão Geral](#overview)
- [Funcionalidades](#features)
- [Estrutura de Ficheiros](#file-structure)
- [Como Funciona](#how-it-works)
- [Como Usar o Kit](#using-the-kit)
- [Converter um Site Estático](#converting-a-static-site)
- [Blog](#blog)
- [Coisas a fazer antes de publicar](#pre-deployment-things)

# Visão Geral
<a name="#overview" />

### Introdução
Este kit tem tudo o que precisa para usar o Netlify CMS personalizado para criar um blog que pode ser editado por clientes numa interface amigável do Netlify. Já tem todos os scripts e configurações prontos a funcionar, só precisa de adicionar o site ao Netlify, ativar o Identity, clicar no botão para ativar o Git Gateway para que, quando o cliente submeter um blog, este seja enviado para o repositório, e está feito. Pode também definir o registo como apenas por convite e adicionar um botão "iniciar sessão com Google" nas opções.

Aqui está um link para uma demonstração ao vivo deste kit no Netlify:
https://starterkit-v4-eleventy.netlify.app/

### Vídeo de Apresentação
Aqui está uma pequena introdução ao novo kit para ver o que há de novo:
<br>
https://youtu.be/JvEXfQGFKu4

# Funcionalidades
<a name="#features" />
Este starter kit tem como objetivo permitir arrancar qualquer projeto no menor tempo possível. Imita um website pré-feito, para que possa fazer modificações onde for necessário e obter um site totalmente funcional e otimizado em poucas horas. Vem com um design totalmente responsivo por defeito e tem algumas funcionalidades extra para uma melhor experiência de desenvolvimento.

Algumas dessas funcionalidades incluem:
- **Eleventy** - O Eleventy permite-lhe usar linguagens de template no seu projeto. Isto permite-lhe potenciar o seu HTML para componentes reutilizáveis e layouts para manter o código mais limpo. A linguagem de template usada neste kit é Nunjucks, mas o Eleventy permite usar várias ao mesmo tempo. Vem também com vários plugins...
- **Eleventy Images**. Com este plugin, já não precisa de perder horas a otimizar e reformatar imagens. Basta usar o shortcode de imagem e o Eleventy otimiza, comprime e converte a imagem para formatos modernos. Se escrever bom código, pode obter pontuações de 90+ no Lighthouse logo à partida.
- **Eleventy Navigation** - Simplifica a criação de navegação para apenas 3 linhas no frontmatter do seu HTML. O resto já está feito.
- **Dados Centralizados** - Para facilitar e acelerar o início e crescimento do projeto, existe uma pasta com informação chave sobre o cliente. Se mais tarde quiser mudar um número de telefone, morada ou nome, está tudo num só sítio.
- **Netlify CMS** - Este kit já vem com um blog, alimentado pelo Netlify CMS. Toda a configuração já está feita.
- **Modo Escuro** - Com o modo escuro a tornar-se comum, tê-lo nos seus sites é um extra interessante. Este kit facilita a adição de estilos escuros. Melhor ainda, as preferências do sistema do utilizador são detetadas na primeira visita, por isso quem já usa modo escuro terá essa versão logo na primeira visita.

Se alguma destas funcionalidades não fizer sentido, não se preocupe! Está tudo explicado na secção [Get Started](). Mas primeiro, é melhor conhecer a estrutura do projeto...

# Estrutura de Ficheiros
<a name="#file-structure" />
Antes de entrar nos detalhes de como usar o kit, é útil perceber como o projeto está organizado, para poder expandi-lo da melhor forma.

### root
Na raiz do projeto, vai encontrar algumas pastas, o .eleventy.js, .gitignore e alguns ficheiros package.json.

De todos os ficheiros, só precisa de se preocupar com o .eleventy.js. Aqui estão as configurações do Eleventy SSG. É neste ficheiro que pode dizer ao Eleventy como otimizar imagens, definir onde estão os componentes, dados e layouts, e também o que entra no build final.

O gitignore mantém as pastas node_modules e public fora do repositório, pois são pastas grandes que não interessam a outros. Falando nisso, para que servem essas pastas?

### public vs src vs node_modules
Destas três pastas, só precisa de se preocupar com uma. A node_modules tem todas as dependências e código extra necessário para o site. A public tem o código pronto para produção do seu site.

Nenhuma destas deve ser modificada. Só precisa de trabalhar na pasta src. Aí tem tudo o que precisa para criar um ótimo site.

### Pastas da Source
Vai trabalhar na pasta src neste projeto. Aqui está tudo organizado para facilitar o seu trabalho.

- **_data** - É um repositório global de dados acessível em todo o projeto. O kit traz um ficheiro client, com informação sobre um cliente potencial. Pode aceder a estes dados usando o nome do ficheiro como objeto, depois as chaves/valores. Por exemplo, para mostrar o nome do cliente: `{{ client.name }}`.
- **_includes e _layouts** - Estas duas pastas permitem funcionalidades de template no Eleventy. Os layouts de página inteira estão em _layouts e podem ser usados no campo 'layout' do frontmatter. _includes tem componentes reutilizáveis, como o header ou footer.
- **admin** - Configuração do CMS. Pode ignorar o index.html, mas o config.yml pode ser útil. Veja mais nos [Netlify Docs]().
- **assets** - Para todos os assets que não sejam HTML/CSS, como SVGs, JavaScript e imagens que não quer otimizar.
- **blog** - Todos os ficheiros markdown das páginas de blog estão aqui. O frontmatter dos posts está em blog.json.
- **CSS** - Neste projeto usamos o pré-processador LESS. Todos os ficheiros LESS e CSS estão aqui.
- **images** - Imagens a otimizar são guardadas aqui, antes de serem transformadas e enviadas para a pasta /public
- **pages** - Todas as páginas que não são a home estão aqui

#### src/images vs assets/images
Pode perguntar-se porque há dois sítios para imagens. Tem a ver com o plugin de imagens do Eleventy. Imagens em src/images são otimizadas e guardadas na pasta /public, com nome alterado. assets/images tem imagens que não quer otimizar.

Como o processo de build muda os nomes das imagens, imagens do CMS não podem ser otimizadas pelo Eleventy. Além disso, algumas imagens, como o logo, não precisam de ser redimensionadas ou otimizadas, por isso ficam aqui.

# Como funciona por trás
<a name="#how-it-works" />

https://youtu.be/UDU38awKQeg

Temos um ficheiro base.html com todo o código que se repete em todas as páginas, como o head, meta tags, navegação, footer, etc. Usamos blocos de template (como pequenas variáveis) para inserir o conteúdo de cada página nesse ficheiro base. Carrega o conteúdo, meta tags, insere links ou outros tags únicos de cada página (como CSS individual), e basicamente preenche os espaços em branco do template base.html.

# Como Usar o Kit
<a name="#using-the-kit" />

### Primeiros Passos
<a name="#getting-started" />
0. Se é a primeira vez que usa este kit, recomendo que leia [este artigo](https://www.hyunbinseo.medium.com/nunjucks-settings-for-vs-code-a0da0dc66b95) sobre configurar o VSCode para Nunjucks, a linguagem de template deste kit. Vai ter acesso a autoformatação, realce de sintaxe e emmet.

1. Clone o repositório, guarde no seu computador e abra-o no seu editor de código. Recomendamos o Visual Studio.
2. Depois de abrir o projeto, abra o terminal no editor. No PC é (CTRL + ~). Depois escreva "npm install" para instalar os módulos necessários.
3. Quando o npm terminar, escreva "npm start" para ligar o projeto e correr o servidor local. Vai aparecer muito texto e no fim verá "Local: http://localhost:8080". Carregue em CTRL e clique no link para abrir o projeto no browser. Quaisquer alterações guardadas vão atualizar em tempo real nesse link.
4. Agora está pronto para começar a editar o kit. Pode usar o template pré-feito, adicionar ficheiros ou começar do zero dentro do kit.

Se fechar o projeto e o voltar a abrir mais tarde, tem de abrir o terminal e correr "npm start" outra vez para iniciar o servidor e compilar o código. Depois clique no link do localhost para abrir de novo. Tem de fazer isto sempre que fechar e reabrir um projeto feito com este kit. Se houver erros, aparecem aqui e indicam onde corrigir.

### Configurar o Eleventy
<a name="#setting-up-eleventy" />
Antes de mexer no HTML e CSS, é melhor fazer já as alterações à configuração do SSG. Se abrir o /.eleventy.js, vai ver um ficheiro de configuração longo. Há algumas coisas a mudar, como indicado no comentário no topo.

A primeira coisa a mudar são as media queries por defeito na função imageShortcode. Na linha 9, deve ver algo assim:

`async function imageShortcode(src, alt, className, loading, sizes = '(max-width: 600px) 400px, 850px')`

A parte que diz `sizes = '(max-width: 600px) 400px, 850px` é a que deve mudar. Isto diz "em dispositivos até 600px de largura, usa a imagem de 400px, em dispositivos maiores usa a de 850px".

Neste site, a maioria das imagens em mobile tem 400px de largura, e no desktop cerca de 850px. Dependendo do seu design, pode mudar isto. Pode ser sobrescrito ao usar o shortcode, mas para poupar tempo, vale a pena definir já o valor por defeito.

A segunda coisa a mudar é o array de larguras que o SSG vai produzir, na linha 17. Por defeito, está definido para 200px, 400px, 850px, 1920px e 2500px. Note que as larguras das media queries têm de aparecer aqui. Quando chama a media query, tem de garantir que a largura da imagem que quer está nesta lista.

Se quiser saber mais sobre o plugin de imagens do Eleventy, veja os [eleventy image docs](https://www.11ty.dev/docs/plugins/image/)

### Configurar dados
O próximo passo é ir a /src/_data/client.json e substituir os valores por defeito pelos do seu projeto. As alterações são refletidas instantaneamente em todo o site.

Se houver conjuntos de dados relacionados ou repetidos durante o desenvolvimento, considere criar um novo ficheiro na pasta _data, para manter os dados centralizados. Assim o seu código fica fácil de manter. Um bom exemplo seria um menu - pode ter os dados do menu num ficheiro menu.json, depois usar um [nunjucks for loop](https://mozilla.github.io/nunjucks/templating.html#for) para iterar pelos itens do menu. Se o cliente pedir uma alteração de preço, já sabe onde procurar.

### Layouts e Componentes
Como referido na secção Estrutura de Ficheiros, há pastas para manter layouts e componentes organizados. Todas as páginas usam o ficheiro base.html em _layouts. Este contém o head, header, footer e uma tag main onde o conteúdo da página é inserido. O header e footer são componentes em _includes.

Grande parte do <head> é preenchida automaticamente ao completar o frontmatter de cada página (próxima secção), mas algumas coisas, como favicons e preloads de fontes, têm de ser ajustadas manualmente.

A tag title também já está pré-configurada, dando um título otimizado para SEO a cada página. O título da home e das páginas interiores é tratado de forma diferente, mas pode ser alterado em base.html

### Adicionar uma nova página

Todas as novas páginas devem ser adicionadas à pasta /pages. Se está a migrar um site antigo para este kit, todas as páginas antigas devem ser adicionadas aqui. Todas!

Na pasta \pages há um ficheiro .txt chamado "_new-page-template". Tem o seguinte código:

```
---
layout: 'base.html' 
description: "Meta description for the page"
metaTitle: 'Title that shows up on social OG tags'
tagTitle: 'Title that shows up on google, and is concatenated with | {{ client.name }}'
preloadImg: '/images/imageName.format'
preloadCSS: '/css/fileName.css'
permalink: 'page/'
eleventyNavigation:
    key: Navigation Name
    order: 1000
---

<!-- Enter html code below -->
```

Colocámos todo o front matter e variáveis com etiquetas para saber o que é cada coisa. Abaixo do comentário "Enter html code here" é onde começa a escrever o html dessa página. Não precisa de incluir o header ou footer, só o html único dessa página. Preencha o frontmatter com a informação correta, mantendo o formato dos paths como no .txt

Se está a adicionar uma página antiga, basta criar um novo ficheiro html, colar o conteúdo do new-page-template.txt no topo e copiar o conteúdo entre as tags <main></main> do site antigo para baixo da linha "<!-- Enter html code below -->". Se não usou <main></main>, copie tudo entre a navegação e o footer e cole abaixo do comentário.

O permalink é o nome do slug da página que aparece no URL. Por exemplo, será www.website/page.

Também, NÃO inclua as tags <main></main> na página. Já estão no ficheiro base.html em /includes. O sistema insere o conteúdo da página dentro das <main></main> do base.html. Por isso não são necessárias nas novas páginas.

### Como usar a Navegação
Com o plugin eleventy navigation, tem uma forma fácil e escalável de criar navegação. No frontmatter, os dados em eleventyNavigation controlam o menu. A key é o nome que aparece na navegação, a order define a ordem dos links, do menor para o maior.

Se não quiser que uma página apareça na navegação, basta não incluir a parte eleventyNavigation no frontmatter.

### Otimizar Imagens
Sempre que quiser usar uma imagem, não faça como normalmente faria. Use o shortcode abaixo. Substitua as maiúsculas pelo que pretende, mantendo as aspas:

`{% image 'DIRECT IMAGE PATH', 'ALT TEXT', 'PICTURE ELEMENT CLASS', 'LAZY/EAGER LOADING', 'IMG MEDIA QUERY'%}`

Exemplo:
`{% image './src/images/portfolio/port1.jpg', 'new hallway', 'cs-picture cs-picture-1', 'lazy', '(max-width: 600px) 200px, 400px'%}`

Algumas notas:
1. O caminho da imagem tem de estar no formato acima, começando por ./src.
2. Tem de incluir toda a informação, exceto a media query da imagem. Se não indicar, usa o valor por defeito do .eleventy.js

#### Ligar a imagens noutros sítios
Pode haver casos em que precisa de usar uma imagem sem o shortcode. Por exemplo, como background-image em CSS ou no preload do frontmatter. Para isso, é importante saber o que acontece ao usar o shortcode.

A imagem é movida para /public/images e renomeada. No .eleventy.js, a estrutura do nome é `{name}-{width}w.{format}`. Por exemplo, uma imagem de 400px chamada picture.jpg passa a ser picture-400w.jpg. É esse nome que deve usar nos URLs. Assim, para usar uma imagem como background em CSS, use `background-image: url(/images/picture-400w.jpg)`.

# Como converter um site estático HTML e CSS para o novo sistema:
<a name="#converting-a-static-site" />
https://youtu.be/v6LaVds4yeU
<br>
No vídeo acima, mostro como transferir um projeto real que precisa de migrar o blog para o sistema Eleventy + Netlify CMS. Explico como transferir ficheiros html e css estáticos para o Eleventy Static Site Generator, separar o header e footer em componentes reutilizáveis para adicionar a todas as páginas, criar um ficheiro base, adicionar as páginas antigas e os antigos posts do blog.

Depois mostro como ligar ao Netlify e ativar o CMS em poucos cliques, publicar tudo e usar. Depois de fazer isto algumas vezes para clientes, torna-se rotina e faz-se rapidamente. Originalmente demorava duas horas, mas neste vídeo consegui em 40 minutos. Com um site simples e prática, pode demorar menos de 30 minutos.

### Mover todos os assets

Coloque as imagens que quer otimizar na pasta /images. Os outros assets ficam em /assets, incluindo imagens não otimizadas. Depois, tem de substituir todas as imagens pelo shortcode {% image ... %}. Isto é mais rápido do que otimizar manualmente as imagens!

### Separar as secções de header e footer

Se está a migrar um site atual para este kit, vá à pasta \_includes onde existe um ficheiro header.html e um footer.html. Basta copiar e colar o html necessário para o header no ficheiro header.html e o código do footer no ficheiro footer.html.

Como definir o estado ativo dinâmico para mostrar em que página está? Eis o código:

```
<!--Main Nav-->
<nav id="navbar-menu">
    <ul>
        <li><a class="{{ 'active' if '' == page.url }}" href="/">Home</a></li>
        <li><a class="{{ 'active' if 'about' == page.url }}" href="/about">About Us</a></li>
        <li><a class="{{ 'active' if 'projects' == page.url }}" href="/projects">Projects</a></li>
        <li><a class="{{ 'active' if 'reviews' == page.url }}" href="/reviews">Reviews</a></li>
        <li><a class="{{ 'active' if 'blog' == page.url }}" href="/blog">Blog</a></li>
        <li><a class="{{ 'active' if 'contact' == page.url }}" href="/contact">Contact</a></li>
    </ul>
</nav>
```

Adicionamos este código `{{ 'active' if '' == page.url }}` a cada link e preenchemos as aspas com o slug da página. Por exemplo, no link da página about, diz "adiciona a classe 'active' a esta tag se o texto entre aspas for igual ao slug da página". Neste caso, o slug é /about. Assim, quando está na página about, page.fileSlug = about, que corresponde ao texto "about". Isto avalia como verdadeiro e a classe .active é adicionada ao link, aplicando o estilo correspondente. Quando copiar o seu header para este ficheiro, copie também este código e coloque-o nas class="" dos links onde quer o estado ativo.

Na home page, deixamos a string vazia. Porque na home não há fileSlug, é só /. Por isso, no link da home, dizemos "se não houver file slug, adiciona a classe active".

Depois disto, não precisa de voltar a mexer, a não ser que queira editar. Vai aparecer em todas as páginas. Por isso, no about.html, não precisa de adicionar nada, só escrever o html único dessa página abaixo da linha "<!-- Enter html code below -->". O Eleventy trata do resto, construindo a página com header e footer.

### Converter caminhos antigos e remover .html dos links

Se copiou o html de um site antigo para uma nova página no kit, faça CTRL + F e substitua todos os caminhos de imagens por /assets/images/. Por exemplo, se os caminhos eram /images/image.jpg, agora devem ser /assets/images/image.jpg. Assim garante que só substitui os caminhos certos e não altera outros por engano.

Porque usamos "/assets/images"? No início do README é referido que /public é onde o código é compilado e de onde o Netlify serve o site. O / no início diz ao Netlify para procurar sempre a partir da raiz do projeto. Se não usar o /, o Netlify procura na pasta da página, não na raiz.

Depois, certifique-se que todos os links no html não têm a extensão .html. O Eleventy não reconhece. Por exemplo, /contact.html deve ser /contact. Faça também um substituir por .html, mas confirme que o front matter e o base.html mantêm a extensão correta. Se for removida por engano, volte a pôr.

Se tiver dúvidas sobre caminhos, pode ver na pasta public e seguir a estrutura (mas não altere nada aí, pois perde as alterações no próximo build!). O 11ty usa um sistema de pastas. /contact aponta para a pasta contact e o Netlify carrega o index.html dessa pasta quando acede a www.website.com/contact. Por isso não usamos .html nos links.

### Manter os mesmos caminhos

Se tem caminhos que não quer mudar para manter o SEO, por exemplo /pearland/pearland-piano-lessons, basta mudar o permalink dessa página no front matter para esse caminho.

```
---
layout: 'base.html'
description: "Meta description for the page"
metaTitle: 'Title that shows up on google searches'
tagTitle: 'About'
preloadImg: '/images/cabinets2-1920w.webp'
preloadCSS: '/css/about.css'
permalink: 'folder/page'
eleventyNavigation:
    key: About Us
    order: 200
---
<!-- Enter html code below -->
```

Normalmente, o permalink é o slug da página (pearland-piano-lessons/), mas se quiser um caminho único, basta pô-lo no permalink. Não ponha barras antes do nome, só uma barra depois, como no exemplo.

# Blog
<a name="#blog" />
### Adicionar um novo post ou migrar um antigo para o novo kit

Na pasta /blog há um ficheiro markdown chamado "blog-template.md". É este que usa para criar novos posts. Tem o seu próprio front matter:

```
---
pageName: blog-template
blogTitle: How Much Does a Solar Panel Installation Cost?
titleTag: How Much Does a Solar Panel Installation Cost?
blogDescription: Curious about solar panel pricing? Find out everything you want
  to know about solar pricing from a transparent solar installation company.
author: Joe Mendez
date: 2022-12-16T19:40:18.253Z
tags:
  - post
  - featured
image: /images/blog/landing.jpg
imageAlt: Kitchen
---
```

Tudo isto está ligado ao ficheiro config.yml na pasta /admin, onde configuramos os campos do CMS que o cliente pode preencher ao criar um blog.

```
collections:
  - name: 'blog'
    label: 'Blog'
    folder: 'src/blog'
    create: true
    slug: '{{pageName}}'
    fields:
      - { label: 'Page-Name-with-dashes-only', name: 'pageName', widget: 'string' }
      - { label: 'Blog Title', name: 'blogTitle', widget: 'string' }
      - { label: 'Title Tag', name: 'titleTag', widget: 'string' }
      - { label: 'Description', name: 'blogDescription', widget: 'string' }
      - { label: 'Author', name: 'author', widget: 'string' }
      - { label: 'Date', name: 'date', widget: 'datetime' }
      - { label: 'Tags', name: 'tags', widget: 'list', default: ['post'] }
      - { label: 'Featured Image', name: 'image', widget: 'image' }
      - { label: 'Image Caption', name: 'imageAlt', widget: 'string' }
      - { label: 'Body', name: 'body', widget: 'markdown' }
```

Repare que os nomes das variáveis do front matter correspondem ao "name:" de cada campo. É aqui que configuramos as opções de input para o cliente criar um blog.

Essas variáveis do front matter em blog-template.md ligam-se a esta configuração. Se quiser adicionar um post manualmente, pode copiar este ficheiro, criar um novo, preencher os campos e colar o conteúdo do blog em markdown por baixo, ou escrever um novo em markdown.

Adicionámos o campo 'Page-Name-with-dashes-only' porque muitas agências de SEO e marketing gostam de escolher o slug e as meta tags. Assim, têm controlo total sobre os dados do blog.

### Migrar um post antigo para o novo blog

Só tem de duplicar o blog-template.md e criar um novo ficheiro markdown com o mesmo nome do slug do blog antigo. Por exemplo, se o slug era "how-to-do-something.html", guarde o novo ficheiro como "how-to-do-something.md" na pasta /blog. Depois preencha o front matter. O pageName será o caminho do post, por exemplo "blog/how-to-do-something". Assim mantém o SEO e evita 404.

Não ponha barras depois do nome. Não é igual ao permalink do new-page-template.txt, é só texto e traços.

Depois de preencher tudo, pode transferir o conteúdo. Se tiver o HTML, pode convertê-lo para markdown aqui: https://www.browserling.com/tools/html-to-markdown e colar o markdown abaixo das variáveis. Ou pode copiar o texto e converter manualmente para markdown. O ideal é converter o HTML, pois não pode ter divs, só tags de texto. Se tiver divs, remova, converta e cole o markdown no novo ficheiro. Depois é só guardar. O blog.css já tem tudo estilizado, por isso imagens, headings e listas ficam logo com bom aspeto.

Depois de publicar, o cliente pode editar estes posts manualmente no CMS.

### Adicionar posts em destaque

Adicionar e trocar posts em destaque é fácil. No front matter do markdown, há uma variável para tags.

```
---
pageName: blog-templateke
blogTitle: Should I do Performing Arts or Get a Real Job?
titleTag: 'Performing Arts High Schools in Houston: a Guide | Some Music Studio'
blogDescription: Something about performing arts.
author: Joe M
date: 2022-07-18T15:46:45.249Z
tags:
  - post
  - featured
image: /assets/images/cabinets2-m.jpg
imageAlt: Solar Panels
---
His etudes and concertos are performed by the world's leading pianists, and they are famed for their difficulty. Not to mention the International Chopin Piano Competition, an annual affair in Warsaw that springboards the careers of many famous pianists.
```

A tag "-featured" é o que faz com que um post apareça na secção de destaque. Se está a migrar posts antigos e quer que um seja destacado, basta adicionar "-featured" na linha abaixo de "-post". Quando o cliente quiser trocar, no CMS tem uma caixa de input para as tags. Só tem de remover "featured" para deixar de ser destaque, ou adicionar "featured" ao post que quer destacar. O CMS trata do resto, basta guardar.

### Remover o ficheiro blog-template.md depois de terminar e antes de publicar as alterações.

Se não o remover, ele aparece como post no CMS e no site. Quando terminar de migrar ou criar os posts, pode apagar o ficheiro template. Não vai precisar dele, pois o cliente vai passar a criar posts pelo CMS.

Se não vai migrar posts antigos, pode apagar o ficheiro antes de publicar. O site tem texto por defeito a dizer que ainda não há posts. Assim que o cliente criar um post, esse texto desaparece.

### Modificar o CMS
Na pasta /admin está o ficheiro config.yml, que controla o CMS. Está praticamente tudo configurado, assumindo que só quer um blog. Pode saber mais sobre as capacidades do CMS aqui: [Netlify CMS Docs](https://www.netlifycms.org/docs/intro/)

Se quiser, pode mudar o logo do CMS para personalizar. Abra o config.yml e procure:

```
local_backend: true
# change url to a link to the image you want to use, no file paths, must be a URL
logo_url: https://d33wubrfki0l68.cloudfront.net/c89899bad974606ce0e0f5d5a95842dc787dcb56/7fe98/assets/images/logo-blue.png
```

Mude o logo_url para o URL do logo do cliente. Não aceita paths de ficheiros, só URLs. Abra o site do cliente, inspecione o logo, abra o link da imagem numa nova aba e copie o URL para substituir no config.yml. Assim, quando o cliente entrar no CMS, vê o logo personalizado.

### Testar o CMS

Depois de migrar ou criar os posts, vale a pena testar antes de publicar. No terminal, pode abrir uma nova janela (ícone de dois retângulos no topo direito). Numa janela, mantenha o servidor dev a correr com `npm start`. Na outra, corra `npx netlify-cms-proxy-server`. Isto corre um servidor dev para o Netlify CMS, acessível em localhost:8080/admin, tal como se estivesse online.

Se aparecerem erros, o mais comum é o porto 8081 estar ocupado. O CMS usa esse porto e não tenta outro. Certifique-se que não há outro servidor a usar o 8081 e tente de novo.

# Coisas a fazer antes de publicar
<a name="#pre-deployment-things" />
### Adicionar o sitemap

Se precisar de criar um sitemap, use esta ferramenta: https://www.xml-sitemaps.com/

Para adicionar o sitemap ao Eleventy, crie um ficheiro sitemap.njk na pasta /src. No topo do ficheiro, adicione o front matter para definir o URL:

```
---
permalink: /sitemap.xml
eleventyExcludeFromCollections: true
---
```

Depois, cole o código do sitemap logo abaixo do front matter. NÃO DEIXE ESPAÇOS entre o front matter e o código do sitemap, senão dá erro "XML declaration allowed only at the start of the document". O front matter é removido na build e o código do sitemap fica no topo. Por isso, não deixe linhas em branco.

```
---
permalink: '/sitemap.xml'
eleventyExcludeFromCollections: true
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset
      xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9
            http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
<url>
```

### Adicionar robots.txt

Já existe um passthrough no ficheiro eleventy.js que permite usar o robots.txt dentro da pasta /src. Por isso, para criar ou migrar um robots.txt, basta colocá-lo na pasta /src.

Certifique-se de adicionar ```Disallow: /admin/``` logo abaixo de ```User-agent: *```. Isto impede que a pasta /admin seja indexada pelo Google, o que é importante para SEO. O ficheiro robots.txt já está incluído por defeito, só tem de adicionar o que for necessário.

**Adicione também o URL do sitemap ao robots.txt**. No ficheiro, há uma linha ```Sitemap: https://www.yourwebsite/sitemap.xml```. Troque "https://www.yourwebsite" pelo URL do site do cliente e guarde.

### Adicionar ficheiro _redirects para o Netlify

Se precisar de redirecionamentos, crie um ficheiro _redirects (sem extensão) e coloque-o na pasta /src. Já existe um ficheiro em branco incluído no kit e o passthrough está configurado.

Para adicionar um redirecionamento, ponha o slug antigo à esquerda e o novo à direita:

```
/old-page /new-page
```

Assim, o link /old-page redireciona para /new-page.

### Ligar o GitHub ao Netlify **IMPORTANTE**

Normalmente é simples, mas neste kit há uma diferença. Ao importar o projeto do GitHub para o Netlify, no passo 3, há uma caixa "publish directory". Às vezes aparece "_site", outras vezes está vazia. Mude para "public". Se não fizer isto, não funciona.
https://youtu.be/v6LaVds4yeU?t=3181

### Ligar o blog ao Netlify

Vídeo de como fazer:
https://youtu.be/v6LaVds4yeU?t=3361

A configuração é fácil:

1. Depois de ligar o GitHub ao Netlify e adicionar domínios, clique em "Identity" no topo.
2. Clique em "Enable Identity"
3. Convide-se a si e ao cliente para o site
4. Em "Identity", clique em "Settings and usage"
5. Em "registration preferences", clique em "edit settings" e mude de público para só por convite
6. Em "enable providers", adicione um fornecedor (por exemplo, Google para login rápido)
7. Ative o "Git Gateway"