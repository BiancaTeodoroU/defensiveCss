# defensiveCss

# Documentação sobre CSS defensivo que seria um conceito que visa prevenir ou reduzir comportamentos inesperados de layout, aplicando-se tanto ao design quanto ao desenvolvimento de interfaces

## Tipos

## Flexbox Wrapping

### CSS flexbox é um dos recursos de layout CSS mais úteis atualmente. É muito bom quando usamos display: flex a um wrapper e vermos os itens filhos ordenados um ao lado do outro.

### Afinal então qual seria o problema?, o problema é que quando não há espaço suficiente, esses itens filhos não serão agrupados em uma nova linha por padrão. E para solucionar esse problema existe uma propriedade CSS chamada flex-wrap: wrap.

    .exemplo {
        display: flex;
    }

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/6375d879-68c6-468a-a96c-76b1fc7983c9)

### Mesmo com somente o display: flex como os itens ainda estão próximos uns dos outros. Para corrigir isso, precisamos permitir os itens ficarem flexiveis.

    .exemplo {
        display: flex;
        flex-wrap: wrap;
    }

![image](https://github.com/BiancaTeodoroU/defensiveCss/assets/101062400/792d836e-872a-42d4-af76-baf1593b09b0)
