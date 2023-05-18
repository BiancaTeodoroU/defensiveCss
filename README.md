# defensiveCss

# Documentação sobre CSS defensivo que seria um conceito que visa prevenir ou reduzir comportamentos inesperados de layout, aplicando-se tanto ao design quanto ao desenvolvimento de interfaces

## Tipos

## Flexbox Wrapping

### CSS flexbox é um dos recursos de layout CSS mais úteis atualmente. É muito bom quando usamos display: flex a um wrapper e vermos os itens filhos ordenados um ao lado do outro.

### Afinal então qual seria o problema?, o problema é que quando não há espaço suficiente, esses itens filhos não serão agrupados em uma nova linha por padrão. E para solucionar esse problema existe uma propriedade CSS chamada flex-wrap: wrap.

    .exemplo {
        display: flex;
    }

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/ce551bc9-79fa-493e-a731-1b666bd19677)

### Mesmo com somente o display: flex como os itens ainda estão próximos uns dos outros. Para corrigir isso, precisamos permitir os itens ficarem flexiveis.

    .exemplo {
        display: flex;
        flex-wrap: wrap;
    }

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/7e20c8fe-e1f4-4d44-aa62-253813b97306)
#### obs: nesse exemplo estou na tela de 443 x 549
