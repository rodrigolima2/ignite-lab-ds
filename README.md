# Ignite Lab - Figma e React
## _Semana Ignite Lab realizado pela Rocketseat_

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Semana focada no desenvolvimento de um Design System, utilizando Figma, React, Storybook
e algumas outras ferramentas.

Abaixo estão todas as anotações que fiz durante as aulas.


## Design System
É um padrão de designs que devem ser utilizados por todo o time, para que não haja por exemplo um hover diferente em diferentes partes do site, ou qualquer outra coisa visual que fuja do padrão. É criada uma biblioteca com os componentes padronizados para que eles possam ser utilizados nos projetos.

## Onde conseguir cores para usar nos projetos
- radix colors
- tailwindcss colors

## Figma

##### Auto Layout
O auto layout no figma funciona como um display flex, para utilizar, basta selecionar os items com a tecla SHIFT, agrupá-los com CTRL + G, e então no menu lateral em design, clicar em auto Layout.

##### Tokens
Verificar o projeto e analisar o que pode ser reaproveitado no projeto, como cores, componentes, input de textos, label, checkbox, titulo, todas essas coisas podem ser reaproveitadas em outras telas.

No Figma, ao clicar em Desktop é possível verificar todas as cores que foram utilizadas na tela, essas cores podem ser renomeadas clicando em style e no +. Ao colocar / cria-se subpastas para que as cores sejam agrupadas, por exemplo gray/500. A partir disso é possível utilizar os plugins do figma para criar uma style guide de cores.

##### Componentes no Figma
É possivél criar componentes no figma, assim como os componentes do React. Ao clicar em um item, no menu superior da tela irá aparecer uma opção "create component", ao clicar será criado um componente daquele item. Ao criar o componente é possível adicionar propriedades através do menu lateral direito. Ao criar uma propriedade é possível fazer conexão dela com um elemento do componete, por exemplo criar uma propriedade text chamada placeholder e conecta-la ao texto do componente. Ao clicar em Resources no Menu superior na parte esquerda, clicar em components, é possível localizar o componente criado e utiliza-lo. 

##### Plugins
É possível adicionar plugins para executar determinada função.
- Phosphor Icons - Permite inserir diversos icones
- color styleguide - Cria uma styleguide mostrando todas as nossas tonalidades de cores por categoria.

##### Dicas de atalhos do Figma
- Tecla A - permite adicionar um frame (página).
- Tecla T - permite inserir um texto.
- Tecla R - permite inserir um retangulo.
- CTRL + G - Agrupa os itens selecionados.
- Tecla K com item selecionado - Diminuí ou Aumenta o tamanho de um item proporcionalmente.
- Tecla ALT com item selecionado - Mostra a distância em pixels em que esta em relação ao outro item, se manter a tecla precionada e usar os direcionais será ajustada essa distância, se segurar SHIFT ajusta de 10 em 10 pixels.
- CTRL + D - copia um item, se copiar mais vezes o próximo item seguirá o mesmo padrão de distanciamento entre eles.
- Para centralizar um item, no menu lateral na parte "design" possuí algumas opções de centralização.
- Segurar o SHIFT enquanto arrasta um item faz com que ele só se mova verticalmente ou horizontalmente.
- 
## World Vector Logo
Site para buscar logo de várias ferramentas, empresas, branchs.

## Tailwind Css
Tailwind Css cria rapidamente sites modernos sem sair do seu HTML. Um framework CSS de primeira utilidade com classes como flex, pt-4, text-center e rotate-90 que podem ser compostas para construir qualquer design, diretamente em sua marcação.

Para utilizá-la basta usar os comandos:

```sh
npm install -D tailwindcss
npx tailwindcss init
```

Também é necessário baixar a extensão no VSCode Tailwind CSS IntelliSense.

## Post CSS
Adicione prefixos e regras CSS usando valores do Can I Use. O autoprefixer usará os dados com base na popularidade atual do navegador e no suporte de propriedade para aplicar prefixos para você.

Para que funcione corretamente é preciso instalar a extensão no VSCode PostCSS Language Support.

## Autoprefixer CSS
Analisa seu CSS e adiciona prefixos de fornecedor a regras CSS usando valores do Can I Use. É recomendado pelo Google e usado pelo Twitter e Taobao.

## StoryBook
É uma ferramente que permite visualizar os componentes funcionando de uma forma isolada. Ele funciona com React, vue, etc. Ao invés de navegar até a tela de usuário, abrir o modal para ver um botão, ou variações da página, listagens de usuário por exemplo, com storybook nós podemos visualizar a aplicação, documentar os componentes para que possa se ter uma visão geral, podendo ser compartilhado com a equipe de produção. É uma das ferramentas mais completas para documentar design system. 

Para configurar o storybook dentro do projeto, rodamos o comando:
```sh
npx sb init --builder @storybook/builder-vite --use-npm
```
neste comando esta sendo utilizado o build com o vite ao invés do webpack babel, é muito mais rápido que o babel. Também esta sendo configurado para utilizar o npm, se utilizar outra ferramenta deverá alterar.

Para visualizar o Storybook deve-se rodar o comando:
```sh
npm run storybook
```

## clsx
Uma biblioteca npm utilizada para facilitar na hora de fazer validações para decidir qual classe irá ser utilizada no elmento.

## Radix Slot
Usado para que o usuário possa decidir qual tag deseja usar no componente e não ficar preso ao componente que foi atribuido inicialmente.

## InputHTMLAttributes<HTMLInputElement>
Pega todos os elementos do html (neste caso da tag Input) e possibilita que ele seja utilizado no componente sem precisar passar várias propriedades.

ex:

```sh
export interface TextInputProps extends InputHTMLAttributes<HTMLInputElement> {}

export function TextInput(props: TextInputProps) {
    return (
            <input
                className={clsx(
                    ''
                )}
                {...props} // props possibilita pegar todos os args passados e coloca-los como atributos da tag input
            />
    );
}
```

## Pattern de Composição do React
Quando trabalhamos com componentes que são um conjunto de vários componentes, ao invés de retornar um componente sozinho, com vários subcomponentes, é melhor exportar mais de um componente que quando juntos podem formar um componente maior com suas variações.

Ao invés de exportar a função que é o Componente, são criadas várias funções que são utilizadas como componentes independentes e eles são agrupados em uma constante que é exportada, dentro dessa constante são recebidos os componentes

## phosphor react
Biblioteca npm de icones.
```sh
npm i phosphor-react
```

## Storybook deployer
Para fazer o deploy do storybook foi utilizado o storybook deployer, rodando o comando para instalar:
```sh
npm i @storybook/storybook-deployer --save-dev
```
e adicionando a seguinte linha de comando no package.json em scripts:
```sh
{
  "scripts": {
    "deploy-storybook": "storybook-to-ghpages"
  }
}
```
para criar uma build para o deploy utiliza-se o comando:
```sh
npm run build-storybook
```
a pasta que será criada após o deploy chamada storybook-static deve ser adicionada ao gitignore.

também deve-se criar um arquivo com a seguinte árvore:
```sh
.github/workflows/deploy-docs.yml
```
Esse arquivo deve conter comandos que serão executados todas as vezes que o código tiver alguma alteração.

## storybook-addon-a11y
Faz com que a UI de componentes tenha acessividade

para instalar:
```sh
npm i @storybook/addon-a11y --dev
```
E então adicionar a seguinte linha de comando no arquivo main.cjs dentro da pasta .storybook:
```sh
module.exports = {
  addons: ['@storybook/addon-a11y'],
};
```

## transform tools/
site que converte um svg para um componente do React.
https://transform.tools/

## Interaction Testing with Storybook
Usado para escrever testes para as stories.

instalação:
```sh
npm install -D @storybook/addon-interactions @storybook/testing-library @storybook/jest jest @storybook/test-runner
```
E então no arquivo, main.cjs dentro da pasta .storybook, adiciona-se o comando:
```sh
module.exports = {
  features: {
    interactionsDebugger: true,
  },
};
```
importar as bibliotecas no arquivo que for utilizar, por exemplo:

dentro do arquivo SignIn.stories.tsx
```sh
import { within, userEvent, waitFor } from '@storybook/testing-library';
import { expect } from '@storybook/jest';
```
E então os testes devem ser passados dentro de uma função chamada play:
```sh
export const Default: StoryObj = {
    play: async ({ canvasElement }) => {
        const canvas = within(canvasElement);

        userEvent.type(canvas.getByPlaceholderText('Digite seu e-mail'), 'rodrigo@gmail.com');
        userEvent.type(canvas.getByPlaceholderText('******'), '12345678');

        userEvent.click(canvas.getByRole('button'));

        await waitFor(() => {
            return expect(canvas.getByText('Login realizado!')).toBeInTheDocument();
        });
    }
}
```
Com isso é possivel realizar testes automátizados na aplicação.

Se o script "test-storybook": "test-storybook" for adicionado em scripts no arquivo package.json, é possível utilizar o comando npm run test-storybook no cmd para que todos os testes sejam realizados.

para rodar deve executar o comando:
```sh
npm run test-storybook
```
para rodar em modo watch:
```sh
npm run test-storybook -- --watch
```

## Mock Service Worker (MSW)
O MSW diferente de outras ferramentas de Mock, não intercepta as requisições HTTP e não permite que elas aconteçam, ele praticamente cria uma API local funcionando dentro dos services workers do nosso Browser. O Service Worker é quase que um local onde podemos executar Javascript dentro do nosso Browser. O MSW cria uma API, uma versão do nosso Back-end dentro do Browser, não é preciso criar um processo rodando nosso back-end no terminal.

O MSW tem integração com o Storybook, para instalar:
```sh
npm i msw msw-storybook-addon -D
```
para iniciar roda-se o comando:
```sh
npx msw init public/
```
onde public é a pasta public do projeto. Adiciona-se a linha de comandos dentro da pasta .storybook em main.cjs logo após features:
```sh
"staticDirs": [
  "../public"
]
```
e adiciona-se o seguinte código dentro do arquivo preview na pasta .storybook:
```sh
import { initialize, mswDecorator } from 'msw-storybook-addon';

// Initialize MSW
initialize();

// Provide the MSW addon decorator globally
export const decorators = [mswDecorator];
```
e então para que possa ser utilizado corretamente, dentro do arquivo do storiebook adicionar:
```sh
import {rest} from 'msw';

//em export default onde fica o title, component, args, argTypes, etc, adicionar
    parameters: {
        msw: {
            handlers: [
                rest.post('/sessions', (req, res, ctx) => {
                    return res(ctx.json({
                        message: 'Login Realizado!'
                    }));
                })
            ]
        }
    }
```

Para não dar log das requisições que não passaram, no arquivo preview.csj em initialize, adicionar:
```sh
initialize({
  onUnhandledRequest: 'bypass'
});
```
