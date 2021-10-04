# Naruto - Batalha Ninja

![cover photo](https://s.aficionados.com.br/imagens/frases-iconicas-dos-personagens-de-naruto_f.jpg)

Para quem não conhece, Naruto é uma série de anime e mangá criada por Masashi Kishimoto que recebeu adaptação para animê em 2002. A trama gira em torno de Naruto Uzumaki, um jovem Ninja que constantemente procura por reconhecimento e tem o sonho de se tornar um Hokage, o líder máximo e mais poderoso de sua vila. Durante a história, ocorrem diversas batalhas Ninjas em prol de algum objetivo, tais como: exames para subir de nível, guerras, missões, entre outras.

Neste exercício, vamos modelar e simular uma batalha entre dois nijas. Leia atentamente as regras e transforme tudo o que está sendo solicitado em classes Java respeitando os princípios da OO que vimos até aqui.

## Jutsu

Jutsu (術; Literalmente significa "habilidades/técnicas") são as artes místicas que um Ninja utiliza na batalha. Para usar uma técnica, o Ninja precisará usar seu chakra. Neste exercício, vamos considerar o chakra como a energia que o Ninja gasta para se manter vivo e atacando.

### Modelagem

1. Modele uma classe Jutsu que possui como atributos a quantidade de chakra que consome quando utilizado e o dano (quantidade de chakra que abate do oponente).
2. Todos os atributos devem ser informados no momento em que o Jutsu é instanciado e não pode ser alterado posteriormente.
3. Sobre o atributo que se refere a quantidade de chakra consumido pelo Jutsu, ele deve ser do tipo `int` e valor 5 deve deve ser o máximo que pode ser atribuído.
4. Sobre o atributo que se refere ao dano (quantidade de chakra que o Jutsu remove do oponente), ele deve ser do tipo `int` e valor 10 deve deve ser o máximo que pode ser atribuído.

## Ninja

Ninjas são o foco principal e a principal potência militar na série. A maioria vem de uma aldeia oculta, alguns dos quais vêm de clãs Ninja especializados, e irão realizar as batalhas do nosso exercício.

### Modelagem 

1. Modele uma classe Ninja que possui como atributos o nome, o chakra que possui e o seu Jutsu principal.
2. Todos os atributos devem ser informados no momento em que o Ninja é instanciado.
1. O chakra do Ninja deve ser do tipo `int` e inicializar com valor 100.
3. O Ninja deve possuir um método `atacar` que recebe como parâmetro o seu Ninja oponente. 
4. O Ninja deve possuir um método `receberGolpe` que recebe por parâmetro um valor do tipo `int` correspondente ao dano do golpe recebido.
5. O método `atacar` deve invocar o método `receberGolpe` do oponente, informando o dano do Jutsu principal do Ninja.
6. O metodo `receberGolpe` deve abater do chakra do Ninja o valor do dano recebido.
7. Quando atacar um oponente, o valor do chakra deve ser atualizado de acordo com o consumo do Jutsu.


## Batalha
1. Modele uma classe Batalha na qual **o único** método público deverá ser o `lutar` que receberá como parâmetro os dois nijas da luta. Segue exemplo de assinatura do método:  `public Ninja lutar(Ninja primeiroNinja, Ninja segundoNinja)`.
2. No método `lutar`, cada Ninja ataca o seu oponente 3 vezes.
3. O método `lutar` deve retornar como Ninja vencedor aquele que possuir o maior chakra ao final da luta.
5. Se houver empate, o Ninja do primeiro parâmetro deve ser retornado como vencedor.

## Regras Gerais

### Uchiha Itachi
![Itachi](https://vignette.wikia.nocookie.net/liberproeliis/images/b/b0/Itachi_render_by_xuzumaki-d49n7va.png/revision/latest/scale-to-width-down/340?cb=20161119225550&path-prefix=pt-br)

Se um dos Ninjas se chamar **Itachi**, ele deve vencer sempre, independentemente do oponente. **Obs: não ouse afirmar que ele não é o melhor de todos.**

### Exemplos de Teste

```Java
@Test
public void deveRetornarNinjaComJutsuMaisForteSeOsDoisGastamOMesmoChakraParaAtacar(){
    Jutsu jutsuNinjaUm = new Jutsu(5, 10);
    Ninja ninjaUm = new Ninja("Naruto", jutsuNinjaUm);

    Jutsu jutsuNinjaDois = new Jutsu(5, 8);
    Ninja ninjaDois = new Ninja("Gaara", jutsuNinjaDois);

    Batalha batalha = new Batalha();

    Ninja ninjaVencedor = batalha.lutar(ninjaUm, ninjaDois);

    Assert.assertSame(ninjaUm, ninjaVencedor);
}

@Test
public void deveAtualizarOChakraDoOponenteDeAcordoComODanoDoJutsoQuandoAtacar() {
    Jutsu jutsuNinjaAtacante = new Jutsu(5, 10);
    Ninja ninjaAtacante = new Ninja("Naruto", jutsuNinjaAtacante);

    Jutsu jutsuNinjaOponente = new Jutsu(5, 8);
    Ninja ninjaOponente = new Ninja("Gaara", jutsuNinjaOponente);

    int nivelChakraEsperado = 90;

    ninjaAtacante.atacar(ninjaOponente);

    Assert.assertEquals(nivelChakraEsperado, ninjaOponente.getChakra());
}

```

# Referências
[Sobre a série](https://naruto-pedia.fandom.com/pt-br/wiki/Naruto_(S%C3%A9rie))

[Chakra](https://naruto.fandom.com/pt-br/wiki/Chakra)

[Jutsu](https://naruto.fandom.com/pt-br/wiki/Jutsu)

## Testes Obrigatórios

* Devem existir **obrigatóriamente** na solução entregue testes unitários com os seguintes nomes:

    - deveRetornarNinjaComJutsuMaisForteSeOsDoisGastamOMesmoChakraParaAtacar
    - deveAtualizarOChakraDoOponenteDeAcordoComODanoDoJutsoQuandoAtacar
    - deveRetornarPrimeiroNinjaComoVencedorQuandoONomeForItachi
    - deveRetornarSegundoNinjaComoVencedorQuandoONomeForItachi
    - deveRetornarPrimeiroNinjaComoVencedorQuandoEmpatar
