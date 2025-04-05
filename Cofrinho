package principal;

import java.util.ArrayList;
import java.util.Scanner;

class Cofrinho {
	// Lista para armazenar moedas adicionadas
    private ArrayList<Moeda> listaMoedas = new ArrayList<>();
    
 // Método para adicionar moeda ao cofrinho
    void adicionar(Moeda m) {
        listaMoedas.add(m);
    }
    
 // Método para remover moeda do cofrinho
    void remover(Moeda m) {
        listaMoedas.remove(m);
    }
    
 // Método para listar todas as moedas presentes no cofrinho
    void listagemMoedas() {
        for (Moeda m : listaMoedas) {
            m.info(); // Exibe as informações de cada moeda
        }
    }
    
 // Método para calcular o total das moedas convertidas para Real
    double totalConvertido() {
        double total = 0;
        for (Moeda m : listaMoedas) {
            total += m.converter(); // Converte cada moeda para Real e soma ao total
        }
        return total;
    }
    
    // Método que retorna uma cópia da lista de moedas para evitar alterações externas
    public ArrayList<Moeda> getListaMoedas() {
        return new ArrayList<>(listaMoedas); // Retorna uma cópia para proteger a lista original
    }

 // Método principal que gerencia o funcionamento do cofrinho
    public static void main(String[] args) {
        Cofrinho cofrinho = new Cofrinho();
        Scanner scanner = new Scanner(System.in);
        
        int opcao;
        do {
        	// Exibe o menu de opções para o usuário
            System.out.println("\nCofrinho de Moedas:");
            System.out.println("1-Adicionar Moeda");
            System.out.println("2-Remover Moeda");
            System.out.println("3-Listar Moedas");
            System.out.println("4-Calcular total convertido para Real");
            System.out.println("0-Encerrar");
            
            while (!scanner.hasNextInt()) { // Tratamento para evitar erro ao inserir letras
                System.out.println("Entrada inválida! Por favor, insira um número inteiro.");
                scanner.next(); // Descarta a entrada inválida
            }
            opcao = scanner.nextInt();

            switch (opcao) {
                case 1:
                	// Adicionar uma moeda ao cofrinho
                	System.out.print("\nEscolha Moeda:\n");
                    System.out.println("1-Real: \n2-Dolar: \n3-Euro:");
                    int tipo;
                    if (scanner.hasNextInt()) {
                    	tipo = scanner.nextInt();
                    }
                    else {
                    	System.out.println("Entrada Inválida!");
                    	scanner.next();
                    	break;
                    }
                    
                    System.out.println("Digite o Valor: ");
                    double valor;
                    if (scanner.hasNextDouble()) {
                    	valor = scanner.nextDouble();
                    }
                    else {
                    	System.out.print("Valor Inválido!\n");
                    	scanner.next();
                    	break;
                    }

                    // Cria a moeda correspondente e adiciona ao cofrinho
                    if (tipo == 1) cofrinho.adicionar(new Real(valor));
                    else if (tipo == 2) cofrinho.adicionar(new Dolar(valor));
                    else if (tipo == 3) cofrinho.adicionar(new Euro(valor));
                    else System.out.println("Tipo inválido.");
                    break;

                case 2:
                    // Remover uma moeda do cofrinho
                    System.out.println("Valor da moeda a remover:");
                    double valorRemover;
                    if (scanner.hasNextDouble()) {
                    	valorRemover = scanner.nextDouble();
                    }
                    else {
                    	System.out.println("Valor Inválido!");
                    	scanner.next();
                    	break;
                    }
                    
                    // Procura a moeda na lista pelo valor informado
                    Moeda moedaRemover = null;
                    for (Moeda m : new ArrayList<>(cofrinho.getListaMoedas())) {
                    	if (Math.abs(m.getValor() - valorRemover) < 0.0001) { // Comparação para evitar imprecisão de ponto flutuante
                            moedaRemover = m;
                            break;
                        }
                    }
                    if (moedaRemover != null)
                        cofrinho.remover(moedaRemover);
                    else
                        System.out.println("Moeda não encontrada.");
                    break;

                case 3:
                    // Listar todas as moedas do cofrinho
                    cofrinho.listagemMoedas();
                    break;

                case 4:
                    // Exibir o total convertido para Real
                    System.out.println("Total convertido para Real: " + cofrinho.totalConvertido());
                    break;

                case 0:
                    // Encerra o programa
                    System.out.println("Final do Programa!");
                    break;

                default:
                    System.out.println("Opção inválida.");
            }
        } while (opcao != 0);

        scanner.close(); // Fecha o scanner para evitar vazamento de recursos
    }
}
