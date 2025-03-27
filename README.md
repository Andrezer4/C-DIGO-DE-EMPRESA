import java.util.Scanner;
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Empresa empresa = new Empresa();

        while (true) {
            System.out.println("\nMenu:");
            System.out.println("1. Adicionar Funcionário");
            System.out.println("2. Remover Funcionário");
            System.out.println("3. Adicionar Produto");
            System.out.println("4. Remover Produto");
            System.out.println("5. Comprar Produto");
            System.out.println("6. Listar Produtos");
            System.out.println("7. Listar Funcionários");
            System.out.println("8. Sair");
            int opcao = scanner.nextInt();
            scanner.nextLine();

            switch (opcao) {
                case 1: {
                    System.out.println("Id do Funcionario: ");
                    int id = scanner.nextInt();
                    scanner.nextLine();
                    System.out.println("Nome do Funcionário: ");
                    String nome = scanner.nextLine();
                    System.out.println("Idade do Funcionário: ");
                    int idade = scanner.nextInt();
                    scanner.nextLine();
                    System.out.println("Gênero do Funcionário: ");
                    String genero = scanner.nextLine();
                    Funcionario f = new Funcionario(id, nome, idade, genero);
                    empresa.adicionarFuncionario(f);
                    break;
                }
                case 2: {
                    System.out.println("ID do Funcionário para remover: ");
                    int id = scanner.nextInt();
                    empresa.removerFuncionario(id);
                    break;
                }
                case 3: {
                    System.out.println("ID do produto: ");
                    int id = scanner.nextInt();
                    scanner.nextLine();
                    System.out.println("Nome do Produto: ");
                    String nome = scanner.nextLine();
                    System.out.println("Quantidade do Produto: ");
                    int quantidade = scanner.nextInt();
                    Produto p = new Produto(id, nome, quantidade);
                    empresa.adicionarProduto(p);
                    break;
                }
                case 4: {
                    System.out.println("ID do Produto para remover: ");
                    int id = scanner.nextInt();
                    empresa.removerProduto(id);
                    break;
                }
                case 5: {
                    System.out.println("ID do produto para comprar: ");
                    int id = scanner.nextInt();
                    System.out.println("Quantidade para comprar: ");
                    int quantidade = scanner.nextInt();
                    empresa.comprarProduto(id, quantidade);
                    break;
                }
                case 6: {
                    empresa.listarProdutos();
                    break;
                }
                case 7: {
                    empresa.listarFuncionarios();
                    break;
                }
                case 8: {
                    System.out.println("Saindo...");
                    return;
                }
                default:
                    System.out.println("Opção inválida. Tente novamente.");
            }
        }
    }
}
    class Funcionario {
    private int id;
    private String nome;
    private int idade;
    private String genero;

    public Funcionario(int id, String nome, int idade, String genero) {
        this.id = id;
        this.nome = nome;
        this.idade = idade;
        this.genero = genero;
    }

    public int getId() {
        return id;
    }

    public String getNome() {
        return nome;
    }

    public int getIdade() {
        return idade;
    }

    public String getGenero() {
        return genero;
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Nome: " + nome + ", Idade: " + idade + ", Gênero: " + genero;
    }
} 

import java.util.ArrayList;

public class Empresa {

    private ArrayList<Funcionario> funcionarios;
    private ArrayList<Produto> produtos;

    public Empresa() {
        funcionarios = new ArrayList<>();
        produtos = new ArrayList<>();
    }
    public void adicionarFuncionario(Funcionario f){
        funcionarios.add(f);
    }
    public void removerFuncionario(int id) {
        funcionarios.removeIf(f -> f.getId() == id);

    }
    public void adicionarProduto(Produto p){
        produtos.add(p);
    }
    public void removerProduto(int id) {
        produtos.removeIf(p -> p.getId() == id);
    }
    public void listarFuncionarios(){
        for (Funcionario f : funcionarios) {
            System.out.println(f);
        }
    }
    public void listarProdutos() {
        for (Produto p : produtos) {
            System.out.println(p);
        }

    }

    public void comprarProduto(int id, int quantidade) {
    }
}

class Produto {
    private int id;
    private String nome;
    private int quantidade;

    public Produto(int id, String nome, int quantidade) {
        this.id = id;
        this.nome = nome;
        this.quantidade = quantidade;
    }

    public int getId() {
        return id;
    }

    public String getNome() {
        return nome;
    }

    public int getQuantidade() {
        return quantidade;
    }

    public void comprarProduto(int quantidade) {
        if (this.quantidade >= quantidade) {
            this.quantidade -= quantidade;
            System.out.println("Compra realizada com sucesso!");
        } else {
            System.out.println("Quantidade insuficiente no estoque.");
        }
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Nome: " + nome + ", Quantidade: " + quantidade;
    }
}
