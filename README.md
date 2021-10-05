# SOLID com GoLang

## Bad Code / Código Ruim

* Rígido: O código é rígido? Ele tem uma camisa de força de tipos e parâmetros autoritários, que dificultam a modificação?
* Frágil: O código é frágil? A menor mudança se espalha pela base do código, causando estragos incalculáveis?
* Imóvel: O código é difícil de refatorar? É uma tecla de distância de um loop de importação?
* Complexo: Existe código para ter código, as coisas têm engenharia excessiva?
* Detalhado: É cansativo usar o código? Quando você olha para ele, consegue dizer o que esse código está tentando fazer?

## SOLID

Em 2002 Robert Martin publicou seu livro, _Agile Software Development, Principles, Patterns, and Practices_. Nele, ele descreveu 5 princípios de design de software reusável, no qual ele chama de princípios SOLID:

* Single Responsibility Principle
* Open / Closed Principle
* Liskov Substitution Principle
* Interface Segregation Principle
* Dependency Inversion Principle

### Single Responsibility Principle / Princípio da Responsabilidade Única

" A class should have one, and only one, reason to change." – Robert C Martin

Sabemos que não existem classes no Go — Em vez disso, temos a noção muito mais poderosa de composição — Mas se você poder ignorar o uso da palavra classe, acho que tera muito mais valor aqui.

Por que é importante que um trecho de código tenha apenas um motivo para alteração? Bem, tão angustiante quanto a ideia de que seu próprio código pode mudar, é muito mais angustiante descobrir que o código do qual seu código depende está mudando sob seus pés. E quando seu código tiver que mudar, ele deve fazer isso em resposta a um estímulo direto, não deve ser vítima de dano colateral.

Portanto, o código que tem uma única responsabilidade tem menos motivos para mudar.

#### Coupling & Cohesion / Acoplamento e Coesão

Duas palavras que descrevem como é fácil ou difícil mudar um pedaço de software são acoplamento e coesão.

Acoplamento é simplesmente uma palavra que descreve duas coisas mudando juntas - um movimento em uma induz um movimento em outra.

No contexto do software, coesão é a propriedade de descrever partes de código que são naturalmente atraídas umas pelas outras.

#### Nome de Pacotes

Em Go, todo o código reside dentro de um pacote, e um pacote bem projetado começa com seu nome. O nome de um pacote é uma descrição de sua finalidade e um prefixo de espaço de nome. Alguns exemplos de bons pacotes da biblioteca padrão Go podem ser:

* _net/http_, que fornece clientes e servidores http.
* _os/exec_, que executa comandos externos.
* _encoding/json_, que implementa a codificação e decodificação de documentos JSON.

Quando você usa os símbolos de outro pacote dentro do seu, isso é feito pela declaração `import`, que estabelece um acoplamento de nível de origem entre dois pacotes. Eles agora se conhecem.

#### Nomes ruins de pacotes

Esse foco em nomes não é apenas pedantismo. Um pacote mal nomeado perde a oportunidade de enumerar seu propósito, se é que algum dia teve um.

O que o _server_ de pacotes oferece? … Bem, um servidor, espero, mas qual protocolo?

O que o pacote _private_ oferece? Coisas que eu não deveria ver? Deve ter algum símbolo público?

E o pacote _common_, assim como seu parceiro no crime, o pacote _utils_, costuma ser encontrado próximo a esses outros criminosos.

Pegar todos os pacotes como esses se torna uma lixeira para a miscelânea, eles mudam com frequência e sem motivo, e por eles terem muitas responsabilidades.

#### Referências

Material de referência: [SOLID Go Design](https://dave.cheney.net/2016/08/20/solid-go-design)
