# DefensiveCss

## Documentação sobre CSS defensivo que seria um conceito que visa prevenir ou reduzir comportamentos inesperados de layout, aplicando-se tanto ao design quanto ao desenvolvimento de interfaces

## Tipos

### Flexbox Wrapping

#### CSS flexbox é um dos recursos de layout CSS mais úteis atualmente. É muito bom quando usamos display: flex a um wrapper e vermos os itens filhos ordenados um ao lado do outro.

#### Afinal então qual seria o problema?, o problema é que quando não há espaço suficiente, esses itens filhos não serão agrupados em uma nova linha por padrão. E para solucionar esse problema existe uma propriedade CSS chamada flex-wrap: wrap.

    .exemplo {
        display: flex;
    }

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/ce551bc9-79fa-493e-a731-1b666bd19677)

#### Conforme for diminuindo a tela, nesse caso estou em 443 x 549 somente usando o display: flex

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/4476196c-bd10-4146-97aa-06d6fc28f559)

#### Mesmo com somente o display: flex como os itens ainda estão próximos uns dos outros. Para corrigir isso, precisamos permitir os itens ficarem flexiveis.

    .exemplo {
        display: flex;
        flex-wrap: wrap;
    }

#### obs: nesse exemplo estou na tela de 443 x 549

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/96ddd9b3-d866-4ed7-963b-5c710a214722)

#### Ou seja se eu tivesse deixado somente o display: flex a nossa imagem conforme o tamanho de tela fosse menor, não iriam ficar agrupados um abaixo do outro por padrão, mas adicionando a propriedade flex-wrap: wrap conforme o tamanho de tela for menor ele vai deixando um item abaixo do outro.

### Image Distortion

#### Algumas vezes acabamos não tendo controle sobre a proporção de uma imagem em uma página da web, pensando em uma solução para quando o usuário carrega uma imagem que não está alinhada com a proporção, vamos ver o seguinte exemplo:

#### Quando o usuário fizer upload de uma imagem de tamanho diferente, ela será esticada, e isso não é bom. Vejá os exemplos com a imagem normal e esticada.

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/426493a1-0523-4508-a858-c4fc29e8e8df)

#### a solução mais fácil pra isso é usar o CSS object-fit. obs: coloquei 2 maneiras que funcionam.

    .exemplo {
        object-fit: cover;
    }

    img {
        object-fit: cover;
    }
#### e você terá esse resultado, é identica a imagem normal, porém essa tendo o object-fit: cover quando o usuário carregar essa imagem ela não esticara.
![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/358b325d-e09f-414f-8f08-49d84202f4a2)

### Long Content

#### Nesse exemplo foi criada uma lista de nomes, nela parece que está tudo certo. Porém como se trata de conteúdo gerado pelo usuário, temos que ter cuidado em como defender o layout, pra caso fique muito longo.

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/c367e5f4-b441-43fd-be71-42d6aceb7dfc)

#### Nos layouts a consistência é importante. Para solucionarmos o problema podemos truncar o nome usando text-overflow e outras propriedades.

    .exemplo {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

#### Texto grande 

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/f6042b69-b140-480a-b16b-6e1479eb3528)

#### usando o text-overflow e outras propriedades 

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/15e1aa51-2eff-42ec-b52b-2ef94a19b170)

### Component Spacing

#### Como desenvolvedores, precisamos sempre levar em conta diferentes comprimentos de conteúdo. Isso significa que o espaçamento deve ser adicionado a um componente, mesmo que pareça desnecessário.

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/743e7698-afa9-4492-ac3f-11ec8c1dcc20)

#### No exemplo abaixo podemos ver como o texto está muito perto da imagem
![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/b9d0acf7-0f66-4bc6-85b1-e4276c00f97b)

#### Neste exemplo, podemos ver que tem um titulo de seção e uma imagem no lado direito.Mas podemos ver abaixo que o texto está muito perto da imagem, nessa situação ja podemos nos lembrar do truncate que usamos anteriormente mas por enquanto vamos nos concentrar no espaçamento.

#### Se o titulo tiver espaçamento e o truncamento de texto, não veremos mais esse problema.

    .exemplo {
        margin-right: 1rem;
    }

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/e69cbf9f-404e-4fc3-94c7-618eac4c6462)



