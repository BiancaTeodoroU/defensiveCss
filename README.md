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

### Auto-fit Vs Auto-fill

#### Ao usar minmax() a função de grade CSS, é importante decidir entre usar as palavras-chave auto-fitou auto-fill. Quando usado incorretamente, pode levar a resultados inesperados.

#### Ao usar minmax() a função, a auto-fit palavra-chave expandirá os itens da grade para preencher o espaço disponível. Enquanto auto-fill manterá o espaço disponível reservado sem alterar a largura dos itens da grade.

#### Auto fill

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/4c80e8f4-2990-4e77-9ee6-ff477d21c715)

#### auto fit

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/b8e69fe1-789f-4d79-addf-428526bed9af)

#### Dito isto, o uso auto-fit pode levar a itens de grade muito amplos, especialmente quando eles são menores do que o esperado. Considere o seguinte exemplo.

    .exemplo {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-gap: 1rem;
    }

#### Se houver apenas um item de grade e auto-fit for usado, o item será expandido para preencher a largura do contêiner.

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/c091115c-c73b-4a27-a7e0-02c67f53a200)

#### Na maioria das vezes, tal comportamento não é necessário, então usar auto-fill é melhor na minha opinião.

    .exemplo {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr))
        grid-gap: 1rem;
    }

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/4cccde0b-d590-4620-ab5c-007c8c9dfff4)

### Background repeat

#### Se repararmos muitas vezes, quando usamos uma imagem grande como plano de fundo, a gente acaba esquecendo de levar em consideração o caso em que o design seja visualizado em uma tela grande. E com isso o plano de fundo será repetido por padrão.

#### Isso geralmente não será visível na tela de um laptop, mas pode ser visto claramente em telas maiores.

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/6765e822-562c-4fc5-b917-e052ff0619f7)

#### Tela de laptop

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/f4fbd8b0-79d8-4105-bd21-fcbce0a12504)

#### Para evitar esse comportamento com antecedência, certifique-se de redefinir background-repeat.

    .exemplo {
        background-image: url('...');
        background-repeat: no-repeat;
    }

#### Usando as propriedades

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/7c7b9d3e-0b92-47be-914a-8e2b3bf68ce2)

### CSS grid fixed values

### Digamos que temos uma grade que contém um aparte e um principal. O CSS fica assim:

    .exemplo {
        display: grid;
        grid-template-columns: 250px 1fr;
        gap: 1rem;
    }

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/63281ab8-3759-49a2-9165-fd8d68e8b074)

#### Tela de celular 

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/e5b2b30e-a3d2-441c-91ac-02e5e3b6007d)

### Isso será interrompido em tamanhos pequenos de viewport devido à falta de espaço. Para evitar esse problema, sempre use uma consulta de mídia ao usar a grade CSS como a acima.

    @media (min-width: 600px) {
        .exemplo {
            display: grid;
            grid-template-columns: 250px 1fr;
            gap: 1rem;
        }
    }

### CSS Variable Fallback

#### Variáveis ​​CSS são bastante utilizadas para usar tanto no css quanto no javascript. Existe uma maneira na qual que podemos aplicar para usá-los de uma forma que não prejudique a experiência, caso o valor da variável CSS esteja vazio por algum motivo.

#### Isso é particularmente útil ao alimentar o valor de uma variável CSS via Javascript. Aqui está um exemplo:

    .exemplo {
        max-width: calc(100% - var(--actions-width));
    }

#### A variável --actions-width está sendo utilizada dentro da calc() função e seu valor vem do Javascript. Vamos supor que o Javascript falhou por algum motivo, o que acontecerá? O max-width irá computar para nenhum.

#### Podemos evitar isso com antecedência e adicionar um valor de fallback ao var().

    .exemplo {
        max-width: calc(100% - var(--actions-width, 70px));
    }
