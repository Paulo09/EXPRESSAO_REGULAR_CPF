# EXPRESSAO_REGULAR_CPF


Conversão de CPF com Expressões Regulares em Python: Um Guia Completo
Entendendo o Problema

Antes de mergulharmos no código, vamos esclarecer o que significa "conversão" de CPF com expressões regulares em Python.

Expressões Regulares: São padrões de busca flexíveis usados para encontrar e manipular texto. Em Python, o módulo re é o principal responsável por isso.
CPF: O Número de Cadastro de Pessoa Física é um documento de identificação individual no Brasil. Tem um formato específico: 11 dígitos, geralmente separados por pontos e hífen.
Por que usar expressões regulares para CPF?

Validação: Verificar se uma string está no formato correto de um CPF.
Extração: Isolar o número do CPF de um texto maior, removendo formatações.
Substituição: Alterar o formato do CPF (por exemplo, remover pontuação).
Construindo a Expressão Regular

Uma expressão regular simples para validar um CPF no formato brasileiro seria:

Python
import re

cpf_pattern = r'\d{3}\.\d{3}\.\d{3}-\d{2}'
Use o código com cuidado.

\d{3}: Exatamente 3 dígitos.
.: Um ponto literal.
-: Um hífen literal.
Exemplos de Uso

Python
def validar_cpf(cpf):
    return bool(re.match(cpf_pattern, cpf))

# Exemplos de uso:
cpf1 = '123.456.789-10'
cpf2 = '12345678910'  # Sem formatação
cpf3 = 'abc12345678910'  # Contém letras

print(validar_cpf(cpf1))  # True
print(validar_cpf(cpf2))  # False (falta a formatação)
print(validar_cpf(cpf3))  # False (contém caracteres não numéricos)
Use o código com cuidado.

Extraindo o Número do CPF

Python
def extrair_cpf(texto):
    match = re.search(cpf_pattern, texto)
    if match:
        return match.group()
    else:
        return None

# Exemplo:
texto = "Meu CPF é 123.456.789-10 e moro em São Paulo."
cpf = extrair_cpf(texto)
print(cpf)  # 123.456.789-10
Use o código com cuidado.

Removendo a Formatação

Python
def remover_formatacao(cpf):
    cpf_sem_formatacao = re.sub(r'[^0-9]', '', cpf)
    return cpf_sem_formatacao

# Exemplo:
cpf_com_formatacao = '123.456.789-10'
cpf_sem_formatacao = remover_formatacao(cpf_com_formatacao)
print(cpf_sem_formatacao)  # 12345678910
Use o código com cuidado.

Validação Completa do CPF

A expressão regular acima apenas verifica o formato. Para uma validação completa, é necessário calcular os dígitos verificadores e compará-los com os do CPF informado. Esse cálculo envolve uma lógica mais complexa e não será detalhado aqui.

Considerações Adicionais

Flexibilidade: A expressão regular pode ser adaptada para permitir diferentes formatos de CPF, como com ou sem espaços.
Performance: Para grandes volumes de dados, é importante otimizar a expressão regular para evitar lentidão.
Segurança: Evite usar expressões regulares para validar dados de entrada de usuários sem outras medidas de segurança, pois elas podem ser burladas.
Em resumo

As expressões regulares são ferramentas poderosas para manipular textos, incluindo CPFs. Com o módulo re do Python, você pode facilmente validar, extrair e formatar números de CPF.

Gostaria de explorar algum desses tópicos com mais profundidade?

Validação completa do CPF: Podemos detalhar o algoritmo para calcular os dígitos verificadores.
Otimização de expressões regulares: Existem técnicas para tornar as expressões mais eficientes.
Aplicações práticas: Podemos ver exemplos de como usar expressões regulares para CPF em projetos reais.
