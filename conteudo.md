# Custom Hooks no React: Como Criar Lógica Reutilizável do Jeito Certo.



### O que são Hooks?

Sabe quando a gente quer guardar algo na memória pra lembrar depois? Hooks são como essas “lembranças” no React.
Eles são funções que ajudam a usar recursos especiais, tipo guardar dados (estado) ou saber quando algo mudou.
Antes deles, a gente precisava usar **classes** (que são mais difíceis de entender).
Com os Hooks, conseguimos fazer as mesmas coisas de um jeito bem mais simples e organizado.
É como brincar de Lego, mas com código!



### Quais os principais tipos de Hooks?

Os hooks mais usados são `useState`, `useEffect` e `useContext`.
Eles já vêm prontos no React e ajudam a deixar a lógica do seu componente mais poderosa e limpa.
Vamos entender cada um com um pouco mais de carinho, tá? 💙



#### `useState`: guardar e mudar informações

Esse hook serve pra guardar algum valor dentro do componente.
Pode ser o nome da pessoa, se um botão foi clicado, quantos likes tem… o que você quiser.
Ele devolve **duas coisas**: o valor atual e uma função pra mudar esse valor.

Exemplo de código:

import { useState } from 'react';

function MeuComponente() {
  const [contador, setContador] = useState(0);

  return (
    <button onClick={() => setContador(contador + 1)}>
      Cliquei {contador} vezes
    </button>
  );
}


💡 *Explicando:*
`contador` é o número atual.
`setContador` é quem muda esse número.
Sempre que você usa `setContador`, o React atualiza a tela com o novo valor.



#### `useEffect`: fazer algo depois que o site aparece ou muda

Esse hook é tipo um "olheiro" do React.
Ele serve pra rodar algum código depois que o componente aparece ou quando algum valor muda.
Muito usado pra **buscar dados**, **criar timers**, ou **adicionar eventos**.

Exemplo de código:

import { useEffect } from 'react';

useEffect(() => {
  console.log("Componente apareceu!");
}, []);


💡 *Explicando:*
Esse `useEffect` vai rodar **só uma vez**, quando o componente aparecer, por causa do `[]`.
Mas dá pra colocar coisas dentro desse array e reagir às mudanças delas:

Exemplo de código:

useEffect(() => {
  console.log("O nome mudou!");
}, [nome]);


📌 *Bônus: limpeza com return!*
Dá pra retornar uma função dentro do `useEffect`. Isso serve pra **limpar** algo que você configurou antes — como remover um `setTimeout`, `eventListener` ou cancelar uma requisição:

Exemplo de código:

useEffect(() => {
  const timer = setTimeout(() => {
    console.log("Executou depois de 3 segundos!");
  }, 3000);

  return () => {
    clearTimeout(timer); // limpa o timer se o componente sair da tela
  };
}, []);




#### `useContext`: compartilhar informação entre componentes

Sabe quando você quer que vários componentes tenham acesso a uma mesma informação (tipo tema claro/escuro)?
O `useContext` é como uma **caixinha mágica** onde você guarda esse valor, e qualquer parte do app pode acessar.

Exemplo de código:

import { useContext } from 'react';
import { ThemeContext } from './context/ThemeContext';

function Botao() {
  const tema = useContext(ThemeContext);
  return <button className={tema}>Clique aqui</button>;
}


💡 *Explicando:*
Você precisa ter criado um contexto com `React.createContext()` e colocado um `<ThemeProvider>` no topo do app.
Depois disso, todo componente que usar `useContext` consegue acessar aquele valor — sem precisar passar por `props`.



### O que são Hooks Customizados?

Às vezes a gente repete o mesmo código várias vezes…
Em vez disso, dá pra criar um Hook personalizado e reutilizar sempre que quiser.
É tipo montar uma receita de bolo e guardar pra outras festas.
Eles ajudam a deixar tudo mais organizado e fácil de entender.
Olha um exemplo simples:

Exemplo de código:

import { useState } from 'react';

function useToggle(valorInicial = false) {
  const [valor, setValor] = useState(valorInicial);
  const alternar = () => setValor(!valor);
  return [valor, alternar];
}


Exemplo de código:

// Usando o hook
const [ligado, alternarLigado] = useToggle();


💡 Agora você tem um botão que liga e desliga com um Hook só seu. Pode usar em vários lugares sem repetir tudo de novo!



### Curtiu? Me acompanha nas redes! 🚀

Se você gostou desse conteúdo e quer aprender mais sobre front-end e React com uma linguagem simples e direta, me segue!
💼 [LinkedIn](https://www.linkedin.com/in/vinícius-mateus-melo-3b053624a)
🐙 [GitHub](https://github.com/vini230403)

Tô sempre postando coisas novas e práticas por lá! Te espero, hein? 😄



### #ReactHooks #DesenvolvimentoWeb #CustomHooks



**Ilustração de capa**: gerado pelo ChatGPT
**Conteúdo gerado por**: ChatGPT e revisões humanas ✅


