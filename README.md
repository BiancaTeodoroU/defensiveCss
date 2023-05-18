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
#### e você terá esse resultado, é identica a imagem normal, porém essa tendo o object-fit: cover quando o usuário fizer download da imagem ela não esticara.
![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/358b325d-e09f-414f-8f08-49d84202f4a2)
