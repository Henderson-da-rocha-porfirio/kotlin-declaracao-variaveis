# Declaracoes de variaveis

1. VAR = VALORES MUTAVEIS
2. VAL = VALORES IMUTAVEIS (equivalente ao Final do Java)

Vamos analisar as diferenças na **declaração de variáveis** entre Kotlin e Java, com base no código fornecido. Veremos as vantagens e simplificações que Kotlin oferece em relação ao Java.

---

## **1. Declaração de Variáveis em Kotlin**
Kotlin apresenta dois principais modificadores para declaração de variáveis: **`val`** e **`var`**.

### **Características de `val` e `var`:**
1. **`val` (imutável):**
   - Semelhante a `final` no Java.
   - Atribuição única (não pode ser reatribuída após inicialização).
   - Exemplo:
     ```kotlin
     val number = 10
     number = 20 // Erro: não é permitido reatribuir
     ```

2. **`var` (mutável):**
   - Pode ser reatribuído, como qualquer variável regular no Java.
   - Exemplo:
     ```kotlin
     var number = 10
     number = 20 // Permitido
     ```

### **Declaração no Código Kotlin**
```kotlin
var number: Int // Mutável
number = 10
number = 20 // Reatribuição permitida

val employee1 = Employee("Lynn Jones", 500) // Imutável
employee1.name = "Lynn Smith" // Pode alterar a propriedade de um objeto mutável

val employee2: Employee
val number2 = 100

if (number < number2) {
    employee2 = Employee("Jane Smith", 400) // Inicialização tardia
} else {
    employee2 = Employee("Mike Watson", 150)
}
```

- **`var` para variáveis mutáveis**: A variável `number` é reatribuída.
- **`val` para valores imutáveis**: `employee1` não pode ser reatribuído, mas suas propriedades podem ser modificadas.
- **Inicialização tardia:** O `employee2` é declarado como `val` e inicializado dentro de um bloco condicional.

---

## **2. Declaração de Variáveis em Java**
No **Java**, as variáveis seguem a seguinte lógica:

1. **`final` (imutável):**
   - Semelhante a `val` no Kotlin.
   - Atribuição única (não pode ser reatribuída após inicialização).
   - Exemplo:
     ```java
     final int number = 10;
     number = 20; // Erro: não é permitido reatribuir
     ```

2. **Variáveis Regulares:**
   - Sem `final`, as variáveis podem ser reatribuídas livremente.
   - Exemplo:
     ```java
     int number = 10;
     number = 20; // Permitido
     ```

### **Equivalente Java do Código Kotlin**
```java
public class Main {
    public static void main(String[] args) {
        int number; // Mutável
        number = 10;
        number = 20; // Reatribuição permitida

        final Employee employee1 = new Employee("Lynn Jones", 500); // Imutável (não pode ser reatribuído)
        employee1.setName("Lynn Smith"); // Propriedades podem ser alteradas

        final Employee employee2; // Declaração tardia
        final int number2 = 100;

        if (number < number2) {
            employee2 = new Employee("Jane Smith", 400); // Inicialização tardia
        } else {
            employee2 = new Employee("Mike Watson", 150);
        }
    }
}

class Employee {
    private String name;
    private final int id;

    public Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getId() {
        return id;
    }
}
```

---

## **3. Diferenças Entre Kotlin e Java**

| Aspecto                   | Kotlin                                      | Java                                        |
|---------------------------|---------------------------------------------|---------------------------------------------|
| **Mutáveis (`var`)**       | `var` permite reatribuição.                | Variáveis regulares permitem reatribuição. |
| **Imutáveis (`val`)**      | `val` impede reatribuição, mas propriedades de objetos podem ser alteradas. | `final` impede reatribuição, mas propriedades podem ser alteradas. |
| **Tipo Inferido**          | O tipo pode ser inferido pelo compilador.  | Tipo deve ser declarado explicitamente.     |
| **Inicialização Tardia**   | Suportada naturalmente com `val`.          | Suportada com `final`, mas requer blocos adicionais. |
| **Verbosidade**            | Mais conciso e legível.                    | Mais verboso devido à necessidade de declaração explícita. |

---

## **4. Vantagens do Kotlin sobre o Java**

1. **Menos Verbosidade:**
   - Kotlin elimina a necessidade de declarações explícitas de tipos em muitos casos, graças à inferência de tipo.
   - Exemplo:
     ```kotlin
     val number = 10 // Tipo inferido como Int
     ```

2. **`val` e `var`:**
   - A distinção clara entre mutabilidade (`var`) e imutabilidade (`val`) torna o código mais fácil de entender e manter.

3. **Inicialização Tardia:**
   - Kotlin permite declarar variáveis imutáveis (`val`) sem inicializá-las imediatamente, desde que sejam inicializadas antes do uso.
   - Em Java, isso exige o uso de `final`, mas ainda requer mais código para garantir inicialização em todas as ramificações do fluxo.

4. **Imutabilidade Mais Clara:**
   - `val` deixa claro que a referência não pode ser alterada após a inicialização, enquanto em Java, o `final` é mais verboso e frequentemente omitido, levando a confusão.

5. **Menos Código Boilerplate:**
   - Em Java, há a necessidade de escrever getters e setters manualmente, enquanto em Kotlin as propriedades são nativas.

---

## **5. Exemplo Comparativo de Declarações**

### **Kotlin**
```kotlin
val number = 10 // Imutável
var mutableNumber = 20 // Mutável

val employee = Employee("John Doe", 1)
employee.name = "Jane Doe" // Permite alterar a propriedade, mas não reatribuir o objeto
```

### **Java**
```java
final int number = 10; // Imutável
int mutableNumber = 20; // Mutável

final Employee employee = new Employee("John Doe", 1);
employee.setName("Jane Doe"); // Permite alterar a propriedade, mas não reatribuir o objeto
```

---

## **Resumo**

| Conceito              | Kotlin                                          | Java                                        |
|-----------------------|-------------------------------------------------|---------------------------------------------|
| **Inferência de Tipo** | Suporte nativo, reduz a necessidade de declarações explícitas. | Não há inferência de tipo.                 |
| **`val` vs. `var`**    | `val` e `var` deixam claro se a variável é mutável ou não. | Usa `final` para imutáveis; menos evidente. |
| **Imutabilidade**      | Propriedades podem ser imutáveis com `val`.     | Requer `final` para garantir imutabilidade. |
| **Simplicidade**       | Menos código para inicializar e declarar variáveis. | Mais verboso e propenso a repetições.       |
