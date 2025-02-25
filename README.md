<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport"
content="width=device-width, initial-scale=1.0">
<title>Página de Teste</title>
</head>
<body>
<h1>Bem-vindo ao GitHub Pages!</h1>
</body>
</html>






        package javaaa;


import java.util.NoSuchElementException;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner financeiro = new Scanner(System.in);
        System.out.println("Seja bem-vindo ao Planejador Financeiro para Professores e Alunos");
      
        while (true) {
            // Menu para selecionar se é Professor ou Aluno
            System.out.println("========= MENU ========\n" +
                               "1) - Professor\n" + 
                               "2) - Aluno\n" +
                               "3) - Sair\n" +
                               "=====================");
            System.out.println("Digite a opção desejada...");

            int opc = 0;
            try {
                opc = financeiro.nextInt();
            } catch ( NoSuchElementException | IllegalStateException e) {
                System.out.println("Digitação inválida, tente novamente...");
                financeiro.next(); // Limpar o scanner
                continue;
            }
            
            switch (opc) {
                case 1:
                case 2:
              
                    // Entrada de dados financeiros
                    System.out.println("Entre com seu salário:");
                    double salario = financeiro.nextDouble();

                    System.out.println("Você recebeu alguma grana extra? Se sim, digite o valor, senão, digite 0:");
                    double granaExtra = financeiro.nextDouble();

                    double saldo = salario + granaExtra;
                    System.out.println("Seu saldo é R$" + saldo + " reais.");

                    // Registro de despesas
                    while (true) { 
                        System.out.println("=== Você teve alguma despesa? ===\n" +
                                           "1) - Inserir despesa\n" +
                                           "=================================");
                            //Contornando erro_1
                            System.out.println("Digite 1-Para inserir despesa, ou digite qualquer outro número para finalizar...");
                     
                        int despesaOpc = financeiro.nextInt();

                        if (despesaOpc == 1) {
                            System.out.println("Qual o valor?");
                            double despesa = financeiro.nextDouble();
                            saldo -= despesa;
                            System.out.println("Seu saldo é R$" + saldo + " reais.");
                            System.out.println("=== Deseja registrar mais alguma despesa? ===\n"+
                                               "1) - Inserir novamente\n" +
                                               "==============================================");
                            //Contornando erro_2
                            System.out.println("Digite 1-Para inserir um novo valor, ou digite qualquer outro número para finalizar...");
                            int maisDespesa = financeiro.nextInt();
                            if (maisDespesa != 1) {
                                break;
                            }
                        } else {
                            break;
                        }
                    }

                    // Finaliza o registro de despesas
                    System.out.println("Programa será finalizado e você tem R$" + saldo + " reais.");

                    // Registro de Sonho/Meta
                    System.out.println("Qual é o seu sonho ou meta?");
                    financeiro.nextLine(); // Consumir a nova linha
                    String sonho = financeiro.nextLine();

                    System.out.println("Qual é o valor do seu sonho?");
                    double valorSonho = financeiro.nextDouble();

                    System.out.println("Quanto você já tem armazenado?");
                    double dinheiroArmazenado = financeiro.nextDouble();

                    double falta = valorSonho - dinheiroArmazenado;
                    System.out.println("Quanto você pode juntar por mês?");
                    double mensal = financeiro.nextDouble();

                    int meses = (int)Math.ceil(falta / mensal);
                    System.out.println("Para alcançar o seu sonho de " + sonho + ", faltam R$" + falta +
                            " reais. Em " + meses + " meses, juntando R$" + mensal + " por mês, você conquistará o(a) " + sonho + ".");
                    break;
                case 3:
                    // Sai do programa
                    System.out.println("Programa encerrado.");
                    financeiro.close();
                    return;
                default:
                    System.out.println("Opção inválida, tente novamente");
            }
        }
    }
}
