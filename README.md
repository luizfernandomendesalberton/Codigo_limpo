# Codigo Limpo - Resumo de Estudo

Este arquivo organiza os principais pontos sobre nomes, comentarios e formatacao no codigo.

## Capitulo 2: Nomes significativos

No capitulo 2, o autor explica como os nomes utilizados dentro do codigo sao extremamente importantes. Muitas vezes, programadores escolhem nomes pequenos, abreviados ou sem significado claro, o que dificulta a leitura do sistema. Bons nomes tornam o codigo quase autoexplicativo.

### Principais ideias

- Os nomes devem revelar intencao.
- Evite nomes confusos e abreviacoes desnecessarias.
- Use nomes que sejam faceis de pronunciar e pesquisar.
- Evite codificacoes antigas no nome, como notacao hungara.
- Classes: prefira substantivos.
- Metodos: prefira verbos (acoes).

### Exemplo (bom x ruim)

```java
// Bom: nomes claros
int nota1, nota2, nota3, media;

// Ruim: nomes curtos e sem contexto
int n1, n2, n3, m;
```

## Comentarios

Segundo o autor, o ideal e que o codigo seja tao claro que quase nao precise de comentarios. Funcoes pequenas, nomes significativos e boa organizacao ajudam muito nisso.

Comentarios sao uteis quando:

- explicam regra de negocio complexa;
- documentam API;
- registram avisos importantes;
- trazem informacoes legais (como licenca).

Comentarios ruins sao redundantes e repetem o que o codigo ja mostra.

### Exemplo de comentario util

```java
// Solicita a primeira nota ao usuario para calcular a media final
int nota1 = Integer.parseInt(
    JOptionPane.showInputDialog(null, "Digite o valor da primeira nota")
);
```

## Formatacao e identacao

O autor destaca que o codigo deve ter aparencia limpa e organizada. Espacamentos, identacao consistente e separacao por blocos melhoram muito a leitura.

### Boas praticas

- Mantenha funcoes relacionadas proximas.
- Use metodos pequenos e com uma responsabilidade.
- Quebre blocos grandes em partes menores.
- Padronize o estilo de identacao.

### Exemplo organizado

```java
class AlunoMedia {

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
                int idade = Integer.parseInt(JOptionPane.showInputDialog("Informe sua idade"));

                char genero = JOptionPane
                    .showInputDialog("Informe seu genero: M para masculino e F para feminino")
                    .charAt(0);

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
                    generoTexto = "Nao identificado";
                }

                String resultado = aprovado ? "Aprovado" : "Reprovado";

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
                        " | Idade: " + idades.get(i) +
                        " | Genero: " + generos.get(i) +
                        " | Media: " + medias.get(i) +
                        " | Resultado: " + resultados.get(i) +
                        "\n";
                }

                JOptionPane.showMessageDialog(null, lista);
            }

            if (menu == 3) {
                int deletar = Integer.parseInt(
                    JOptionPane.showInputDialog("Digite o codigo do aluno para remover")
                );

                if (deletar >= 0 && deletar < nomes.size()) {
                    nomes.remove(deletar);
                    idades.remove(deletar);
                    generos.remove(deletar);
                    medias.remove(deletar);
                    resultados.remove(deletar);

                    JOptionPane.showMessageDialog(null, "Aluno removido");
                } else {
                    JOptionPane.showMessageDialog(null, "Opcao invalida: " + deletar);
                }
            }

            if (menu > 4) {
                JOptionPane.showMessageDialog(
                    null,
                    "Valor inserido errado",
                    "Caixa de mensagem",
                    JOptionPane.ERROR_MESSAGE
                );
            }
        } while (menu != 4);

        JOptionPane.showMessageDialog(null, "Processo finalizado");
    }
}
```
