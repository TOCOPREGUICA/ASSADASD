# Análise de Mal Design <h1>

## 1. Violação do Princípio da Inversão de Dependência (DIP)

**Problema:**  
A classe `Switch` depende diretamente da classe concreta `LightBulb`, o que gera um acoplamento forte. Isso viola o princípio da Inversão de Dependência (DIP), onde classes de alto nível não devem depender de classes de baixo nível, mas sim de abstrações.

**Solução:**  
Fazer a classe `Switch` depender de uma abstração (interface ou classe abstrata) em vez de depender diretamente de `LightBulb`.

---

## 2. Violação de "God Class"

**Problema:**  
A classe `Application` assume muitas responsabilidades, tornando-se uma "God Class", violando o princípio da Responsabilidade Única (SRP). Cada método da classe `Application` realiza uma tarefa independente (autenticação, carregamento de dashboard, processamento de pagamentos, etc.), dificultando a manutenção e expansão.

**Solução:**  
Dividir essas responsabilidades em classes menores e mais específicas, cada uma com uma única responsabilidade.

---

## 3. Dependências Codificadas (Hard-Coded)

**Problema:**  
A classe `Report` tem dependências codificadas diretamente, tornando-se inflexível. A implementação está atrelada a um tipo específico de relatório (PDF), dificultando a expansão para outros tipos.

**Solução:**  
Usar uma abordagem baseada em interfaces, permitindo que diferentes tipos de geradores de relatórios sejam passados para a classe `Report`.

---

## 4. Tratamento Inadequado de Exceções

**Problema:**  
A exceção genérica `Exception` está sendo capturada, ocultando erros específicos e dificultando a depuração. Além disso, a mensagem de erro fornecida é genérica e não oferece informações suficientes sobre o problema.

**Solução:**  
Capturar exceções específicas (como `ArithmeticException`) e fornecer mensagens de erro mais detalhadas. Além disso, lançar exceções adequadas em vez de apenas capturar e ignorar erros.

---

## 5. Violação do Princípio da Segregação de Interface (ISP)

**Problema:**  
A interface `Machine` é muito genérica, forçando a implementação de métodos que nem todas as classes precisam.

**Solução:**  
Dividir a interface `Machine` em interfaces menores e mais específicas, permitindo que as classes implementem apenas o que realmente necessitam.

---

## 6. Violação do Princípio da Substituição de Liskov (LSP)

**Problema:**  
A classe `Ostrich` herda de `Bird`, mas sobrescreve o método `fly()` lançando uma exceção. Isso viola o LSP, pois uma subclasse deve poder substituir a superclasse sem alterar o comportamento esperado.

**Solução:**  
Criar uma hierarquia separada para aves que voam e aves que não voam, garantindo que apenas classes adequadas implementem o método `fly()`.

---

## 7. Violação do Princípio Aberto-Fechado (OCP)

**Problema:**  
A classe `DiscountCalculator` precisa ser modificada sempre que um novo tipo de cliente é adicionado (exemplo: "SuperVIP"). Isso viola o OCP, pois a classe deveria estar aberta para extensão, mas fechada para modificação.

**Solução:**  
Utilizar o padrão Strategy, criando uma interface para os tipos de desconto, permitindo adicionar novos tipos sem alterar `DiscountCalculator`.

---

## 8. Violação do Princípio da Responsabilidade Única (SRP)

**Problema:**  
A classe `Invoice` assume múltiplas responsabilidades: gerenciar dados da fatura, imprimir a fatura e salvar no banco de dados.

**Solução:**  
Separar as responsabilidades em classes distintas, como `Invoice`, `InvoicePrinter` e `InvoiceRepository`, garantindo que cada classe tenha apenas uma função específica.

---

## 9. Violação de Acoplamento Forte (Tight Coupling)

**Problema:**  
A classe `Car` depende diretamente da implementação concreta de `Engine`, criando um forte acoplamento.

**Solução:**  
Criar uma interface `EngineInterface` e fazer com que `Car` dependa dessa abstração, permitindo diferentes implementações de motor sem modificar a classe `Car`.

---

## 10. Violação da Encapsulação

**Problema:**  

- **Violção do SRP:** A classe `Person` expõe atributos públicos (`name` e `age`), permitindo que qualquer código externo os modifique diretamente.  
- **Violção do OCP:** Como os atributos são públicos, qualquer mudança na forma de manipulação exigirá alterações diretas na classe.  
- **Violção do DIP:** O código principal (`main`) depende diretamente da implementação concreta de `Person`, quebrando a ideia de um design flexível e desacoplado.

**Solução:**  

- Encapsular os atributos `name` e `age`, tornando-os privados e acessíveis via métodos `get` e `set`.  
- Criar uma interface `PersonInterface` ou uma classe base para maior flexibilidade na expansão.

