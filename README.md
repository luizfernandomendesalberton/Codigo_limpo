# Código Limpo - Resumo

## Capítulo 2: Nomes significativos

No capítulo 2, o autor explica como os nomes utilizados dentro do código são extremamente importantes. Muitas vezes, programadores escolhem nomes pequenos, abreviados ou sem significado claro, o que acaba dificultando a leitura do sistema. Segundo o autor, bons nomes tornam o código praticamente autoexplicativo.

Uma das principais ideias apresentadas é que os nomes devem revelar a intenção daquilo que estão representando. Por exemplo, uma variável chamada `x` não informa praticamente nada sobre o seu objetivo, enquanto um nome como `quantidadeFuncionarios` já deixa claro qual informação está sendo armazenada. Isso facilita muito para quem irá ler o código depois.

O autor também comenta sobre evitar nomes que possam causar confusão. Utilizar palavras muito parecidas para funções diferentes ou abreviações desnecessárias pode gerar erros e dificultar a manutenção do sistema. Além disso, ele destaca que nomes precisam ser fáceis de pronunciar e pesquisar, pois durante o desenvolvimento os programadores conversam sobre o código e procuram trechos específicos com frequência.

Outro ponto importante apresentado no capítulo é evitar codificações antigas nos nomes, como prefixos técnicos ou notações húngaras. Em vez disso, deve-se utilizar nomes simples e claros. O autor também explica que classes normalmente devem possuir nomes de substantivos, enquanto métodos devem utilizar verbos que indiquem ações.

### Exemplo

```java
// Correto: nomes claros
int nota1, nota2, nota3, media;

// Errado: nomes curtos e sem contexto
int n1, n2, n3, m;
```

## Comentários

Segundo o autor, o ideal é que o código seja escrito de forma tão clara que quase não precise de comentários. Funções pequenas, nomes significativos e boa organização ajudam muito nisso. Ele comenta que comentários não devem ser usados para “salvar” códigos ruins.

Mesmo assim, o capítulo também mostra que existem comentários úteis em algumas situações. Comentários podem ser importantes para avisos específicos, documentação de APIs, explicações de regras de negócio muito complexas ou informações legais, como licenças de software.

O autor critica principalmente comentários redundantes ou desnecessários. Muitas vezes os programadores escrevem comentários que apenas repetem o que já está evidente no código. Isso não agrega valor e ainda pode gerar problemas futuros caso o comentário fique desatualizado enquanto o código é alterado.

### Exemplo de comentário

```java
// Solicita ao usuário a primeira nota para cálculo da média
int nota1 = Integer.parseInt(
    JOptionPane.showInputDialog(null, "Digite o valor de sua primeira nota")
);
```

## Formatação

O autor destaca que o código deve possuir uma aparência limpa e organizada. Espaçamentos corretos, indentação adequada e separação entre blocos de código ajudam bastante na leitura. Quando o código está bem estruturado visualmente, fica mais fácil identificar funções, condições, laços de repetição e responsabilidades de cada parte do sistema.

Outro ponto importante é manter conceitos relacionados próximos uns dos outros. Funções que trabalham juntas devem ficar organizadas de maneira lógica, facilitando o entendimento do fluxo do programa.

O capítulo também fala sobre a importância de funções pequenas. Métodos muito grandes acabam ficando difíceis de entender e manter. Já funções menores tornam o sistema mais organizado e facilitam testes e correções.

### Exemplo de boa identação

```java
class alunoMedia {

    public static void main(String[] args) {
        ArrayList<String> nomes = new ArrayList<>();
        ArrayList<Integer> idades = new ArrayList<>();
        ArrayList<String> generos = new ArrayList<>();
        ArrayList<Integer> medias = new ArrayList<>();
        ArrayList<String> resultados = new ArrayList<>();

        int menu;

        do {
            menu = Integer.parseInt(
                JOptionPane.showInputDialog(
                    null,
                    "1 - Adicionar aluno\n" +
                    "2 - Lista de alunos\n" +
                    "3 - Remover alunos\n" +
                    "4 - Sair"
                )
            );

            if (menu == 1) {
                String nome = JOptionPane.showInputDialog("Informe seu nome");
                int idade = Integer.parseInt(JOptionPane.showInputDialog("informe sua idade"));

                char genero = JOptionPane.showInputDialog(
                    "informe seu genero M para masculino e F para feminino"
                ).charAt(0);

                int nota1 = Integer.parseInt(JOptionPane.showInputDialog("Informe a primeira nota"));
                int nota2 = Integer.parseInt(JOptionPane.showInputDialog("Informe a segunda nota"));
                int nota3 = Integer.parseInt(JOptionPane.showInputDialog("Informe a terceira nota"));

                int media = (nota1 + nota2 + nota3) / 3;
                boolean aprovado = media >= 6;

                String generoTexto;
                if (genero == 'F' || genero == 'f') {
                    generoTexto = "Feminino";
                } else if (genero == 'M' || genero == 'm') {
                    generoTexto = "Masculino";
                } else {
                    generoTexto = "nao identificado";
                }

                String resultado;
                if (aprovado) {
                    resultado = "Aprovado";
                } else {
                    resultado = "Reprovado";
                }

                nomes.add(nome);
                idades.add(idade);
                generos.add(generoTexto);
                medias.add(media);
                resultados.add(resultado);
            }

            if (menu == 2) {
                String lista = "";

                for (int i = 0; i < nomes.size(); i++) {
                    lista += i + " - " +
                        "Nome: " + nomes.get(i) +
                        " Idade: " + idades.get(i) +
                        " Genero: " + generos.get(i) +
                        " Media: " + medias.get(i) +
                        " Resultado: " + resultados.get(i) +
                        "\n";
                }

                JOptionPane.showMessageDialog(null, lista);
            }

            if (menu == 3) {
                int deletar = Integer.parseInt(
                    JOptionPane.showInputDialog("Digite o codigo do aluno para deletar")
                );

                if (deletar >= 0 && deletar < nomes.size()) {
                    nomes.remove(deletar);
                    idades.remove(deletar);
                    generos.remove(deletar);
                    medias.remove(deletar);
                    resultados.remove(deletar);

                    JOptionPane.showMessageDialog(null, "Aluno removido");
                } else {
                    JOptionPane.showMessageDialog(null, "Opção invalida" + deletar);
                }
            }

            if (menu > 4) {
                JOptionPane.showMessageDialog(
                    null,
                    "valor inserido errado",
                    "Caixa mensagem",
                    JOptionPane.ERROR_MESSAGE
                );
            }
        } while (menu != 4);

        JOptionPane.showMessageDialog(null, "Processo finalizado");
    }
}
```
