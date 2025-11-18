#include <iostream>
#include <vector>
#include <list>
#include <set>
#include <map>
#include <string>
#include <algorithm>
using namespace std;

// Classe Produto
class Produto {
public:
    string nome;
    string categoria;
    double preco;
    int estoque;

    Produto(string n, string c, double p, int e)
        : nome(n), categoria(c), preco(p), estoque(e) {}

    void exibir() const {
        cout << "- " << nome
             << " | Categoria: " << categoria
             << " | Preço: R$" << preco
             << " | Estoque: " << estoque << endl;
    }
};

int main() {
    vector<Produto> produtos;
    set<string> categorias;
    map<string, int> produtos_por_categoria;
    map<string, double> valor_por_categoria;
    list<string> historico_vendas;

    cout << "=== SISTEMA DE INVENTÁRIO DE LOJA (STL) ===\n\n";

    // ---------------------
    // 1. ADICIONAR PRODUTOS
    // ---------------------
    produtos.push_back(Produto("Cafeteira Elétrica", "Eletrodomésticos", 199.90, 12));
    produtos.push_back(Produto("Liquidificador Turbo", "Eletrodomésticos", 159.50, 8));
    produtos.push_back(Produto("Boné Azul", "Acessórios", 29.99, 25));
    produtos.push_back(Produto("Pulseira de Couro", "Acessórios", 49.90, 18));
    produtos.push_back(Produto("Caneta Azul Premium", "Papelaria", 8.50, 60));
    produtos.push_back(Produto("Bloco de Notas A5", "Papelaria", 14.90, 40));

    cout << "--- Produtos cadastrados ---\n";
    for (const auto& p : produtos) {
        p.exibir();
    }

    // Registrar categorias e estatísticas
    for (const auto& p : produtos) {
        categorias.insert(p.categoria);
        produtos_por_categoria[p.categoria]++;
        valor_por_categoria[p.categoria] += p.preco * p.estoque;
    }

    // --------------------------
    // 2. BUSCAR PRODUTO POR NOME
    // --------------------------
    string busca = "Bloco de Notas A5";
    cout << "\n--- Buscando produto: '" << busca << "' ---\n";

    auto it = find_if(produtos.begin(), produtos.end(),
        [&](const Produto& p) { return p.nome == busca; });

    if (it != produtos.end()) {
        cout << "Produto encontrado:\n";
        it->exibir();
    } else {
        cout << "Produto não encontrado.\n";
    }

    // -------------------------------------
    // 3. LISTAR PRODUTOS DE UMA CATEGORIA
    // -------------------------------------
    string categoria_busca = "Acessórios";
    cout << "\n--- Produtos da categoria '" << categoria_busca << "' ---\n";

    for (const auto& p : produtos) {
        if (p.categoria == categoria_busca) {
            p.exibir();
        }
    }

    // --------------------------------------
    // 4. CALCULAR VALOR TOTAL DO INVENTÁRIO
    // --------------------------------------
    double total_inventario = 0;
    for (const auto& par : valor_por_categoria) {
        total_inventario += par.second;
    }

    cout << "\nValor total do inventário: R$" << total_inventario << endl;

    // ---------------------------
    // 5. REGISTRAR UMA VENDA
    // ---------------------------
    string vendido = "Cafeteira Elétrica";
    cout << "\n--- Registrando venda de: " << vendido << " ---\n";

    for (auto& p : produtos) {
        if (p.nome == vendido && p.estoque > 0) {

            p.estoque--;
            historico_vendas.push_back(vendido);

            produtos_por_categoria[p.categoria]--;
            valor_por_categoria[p.categoria] -= p.preco;

            cout << "Venda registrada!\n";
            break;
        }
    }

    // Histórico de vendas
    cout << "\n--- Histórico de vendas ---\n";
    for (const auto& nome : historico_vendas) {
        cout << "- " << nome << endl;
    }

    // Estatísticas finais
    cout << "\n=== ESTATÍSTICAS FINAIS ===\n";

    cout << "Categorias cadastradas: \n";
    for (const auto& c : categorias) {
        cout << "- " << c << endl;
    }

    cout << "\nProdutos por categoria:\n";
    for (const auto& par : produtos_por_categoria) {
        cout << par.first << ": " << par.second << endl;
    }

    cout << "\nValor total por categoria:\n";
    for (const auto& par : valor_por_categoria) {
        cout << par.first << ": R$" << par.second << endl;
    }

    return 0;
}
