# Desafio Técnico: Calculadora Completa no Terminal (Python)

Crie uma **calculadora de linha de comando (CLI)** em Python com o máximo de funcionalidades que uma calculadora moderna oferece, priorizando **corretude**, **boa arquitetura**, **testes** e **bom UX no terminal**. O projeto deve ser organizado, documentado e fácil de executar.

---

## 🎯 Objetivos do Desafio
- Implementar uma **calculadora científica completa** que roda no terminal, com:
  - Operações básicas, científicas e utilitários (memória, histórico, conversões, etc.).
  - **Parser de expressões** com precedência, parênteses e funções.
  - **Modo interativo (REPL)** e **modo por argumento** (avaliar expressão passada na linha de comando).
  - **Tratamento robusto de erros** e **precisão configurável**.
- Entregar **código limpo**, **testes automatizados** e **documentação clara**.

---

## ⚙️ Escopo Funcional

### 1) Operações Aritméticas Básicas
- Soma `+`, Subtração `-`, Multiplicação `*`, Divisão `/` (com divisão por zero tratada).
- Exponenciação `^` ou `**` e Radiciação `sqrt(x)` e `root(n, x)`.
- Módulo `mod`, resto `%`, divisão inteira `//`.
- Negativo/positivo unário (ex.: `-3 * (-2)`).

### 2) Precedência, Parênteses e Associação
- Suporte a `()`, regras de **ordem de operações** e **associatividade**.

### 3) Funções Científicas
- Trigonométricas: `sin`, `cos`, `tan` (e inversas `asin`, `acos`, `atan`).
- Hiperbólicas: `sinh`, `cosh`, `tanh`.
- Logaritmos: `ln`, `log10`, `log(base, x)`.
- Potências: `pow(x,y)`, `exp(x)`.
- Fatoriais: `fact(n)` e `gamma(x)`.
- Combinatória: `nCr(n, r)`, `nPr(n, r)`.
- Percentuais: `50%`, `200 + 10%`, `x% of y`.
- Arredondamentos: `round`, `ceil`, `floor`, `trunc`.
- Valores absolutos: `abs(x)`.
- Constantes: `pi`, `e`, `tau`.

### 4) Conversões de Unidades
- Ângulo: `deg2rad(x)`, `rad2deg(x)`.
- Temperatura: `c2f`, `f2c`, `c2k`, `k2c`.
- Comprimento: `m2km`, `km2m`, `in2cm`, `cm2in`.
- Massa: `kg2lb`, `lb2kg`.
- *(Bônus)*: tempo, velocidade, bytes ⇄ MB/GB, etc.

### 5) Memória e Histórico
- **Memória**: `MS`, `MR`, `M+`, `M-`, `MC`.
- **Histórico**: `history`, `!3`, `clear history`.

### 6) Variáveis e “ANS”
- `x = 2`, `y = 3`, `x + y^2`.
- `ans` guarda o último resultado.
- Persistência opcional (`.calcvars.json`).

### 7) Modos de Operação
- **REPL (interativo)**: `calc`.
- **Argumento direto**: `calc "2*(3+4)"`.
- **Arquivo de script**: `calc -f comandos.calc`.

### 8) Precisão e Formatação
- Precisão configurável (`--precision 12`).
- Modo científico (`--sci`).

### 9) Ajuda e UX
- `--help`, `help`, `functions`, `constants`, `vars`, `history`.
- (Bônus) Autocompletar via `readline`.

### 10) Tratamento de Erros
Mensagens claras para:
- Sintaxe inválida  
- Função desconhecida  
- Divisão por zero  
- Domínio inválido (`sqrt(-1)` sem modo complexo)  
- Overflow  
- etc.

---

## 🧱 Restrições Técnicas
- ❌ Não usar `eval` nem `ast.literal_eval`.
- Implementar **parser próprio** (Shunting Yard ou recursivo).
- Projeto modular:
  ```
  calc/
    src/
      calc/
        cli.py
        lexer.py
        parser.py
        evaluator.py
        builtins.py
        memory.py
        history.py
        env.py
        errors.py
        format.py
    tests/
  ```
- Cobrir funções com **testes unitários** (PyTest ou unittest).
- Linting e formatação (Ruff + Black).
- Usar apenas bibliotecas padrão (`math`, `decimal`, `fractions`, etc.).

---

## 💻 Exemplos de Uso

```bash
> 2 + 3 * 4
14
> (2 + 3) * 4
20
> sqrt(144) + pow(2, 8)
272
> sin(90)
1
> mode deg
OK
> log(2, 8)
3
> fact(10)
3628800
> nCr(52, 5)
2598960
> 200 + 10%
220
> x = 2
OK
> y = 10
OK
> y % x
0
> MS
OK
> MR * 5
1100
> history
1: 2 + 3 * 4 => 14
> !2
20
> deg2rad(180)
3.141592653589793
> c2f(0)
32
> precision 6
OK
> pi
3.14159
> quit
```

---

## ✅ Requisitos Não-Funcionais
- Rápido, estável e compatível com Python 3.10+.
- Cobertura mínima: 80%.
- Lint/format sem erros.

---

## 📦 Como Executar
```bash
python -m venv .venv
source .venv/bin/activate
pip install -e .

# Modo interativo
calc

# Expressão direta
calc "2*(3+4)"

# Testes
pytest -q
```

---

## 🧪 Testes Mínimos
- [ ] `2+2 == 4`
- [ ] `sqrt(81) == 9`
- [ ] `(2+3)*4 == 20`
- [ ] `sin(90)==1`
- [ ] `log(2,8)==3`
- [ ] `fact(5)==120`
- [ ] `200+10%==220`
- [ ] `deg2rad(180)==pi`
- [ ] `MS`, `MR`, `M+`, `M-`, `MC`
- [ ] `x=2; y=3; x+y==5`
- [ ] Erros: `sqrt(-1)`, `1/0`, etc.

---

## 🌟 Bônus
- Modo de números complexos  
- Definição de funções pelo usuário  
- Histórico persistente  
- Internacionalização (PT/EN)  
- Sistema de plugins  
- Benchmark

---

## 🧭 Diretrizes de Avaliação
| Critério | Peso |
|----------|------|
| Corretude Matemática | 30% |
| Arquitetura & Código | 25% |
| UX no Terminal | 20% |
| Testes & Qualidade | 15% |
| Extras (Bônus) | 10% |

---

## 💬 Observações Finais
Este desafio mede **sua capacidade de estruturar um projeto sólido**, com parsing próprio, boa experiência no terminal e cobertura de testes.  
Explique decisões, trade-offs e extensões futuras no README final do repositório.
