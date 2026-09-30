# AP1

import pytest
from main import *


# ==========================================
# QUESTÃO 1 - IMC
# ==========================================

def test_imc_abaixo_peso():
    resultado = classificar_imc(17)
    assert resultado == "Abaixo do peso"


def test_imc_peso_normal():
    resultado = classificar_imc(22)
    assert resultado == "Peso normal"


def test_imc_acima_peso():
    resultado = classificar_imc(30)
    assert resultado == "Acima do peso"


def test_imc_fronteira():
    resultado = classificar_imc(18.5)
    assert resultado == "Peso normal"


# ==========================================
# QUESTÃO 2 - SAQUE
# ==========================================

def test_saque_valido():
    resultado = sacar(100, 40)
    assert resultado == 60


def test_saque_invalido():
    with pytest.raises(ValueError):
        sacar(100, 150)


# ==========================================
# QUESTÃO 3 - FRETE
# ==========================================

def test_frete_abaixo_5kg():
    resultado = calcular_frete(3)
    assert resultado == 10.0


def test_frete_entre_5_e_10kg():
    resultado = calcular_frete(7)
    assert resultado == 20.0


def test_frete_acima_10kg():
    resultado = calcular_frete(15)
    assert resultado == 35.0


def test_frete_fronteira_5kg():
    resultado = calcular_frete(5)
    assert resultado == 10.0


def test_frete_fronteira_10kg():
    resultado = calcular_frete(10)
    assert resultado == 20.0


# ==========================================
# QUESTÃO 4 - SENHA
# ==========================================

def test_senha_valida():
    resultado = senha_valida("senha123")
    assert resultado == True


def test_senha_curta():
    resultado = senha_valida("abc12")
    assert resultado == False


def test_senha_sem_numero():
    resultado = senha_valida("abcdefgh")
    assert resultado == False


def test_senha_exatamente_8_caracteres():
    resultado = senha_valida("senha123")
    assert resultado == True


# ==========================================
# QUESTÃO 5 - DESCONTO
# ==========================================

def test_desconto_valido():
    resultado = aplicar_desconto(100, 20)
    assert resultado == 80


def test_desconto_zero():
    resultado = aplicar_desconto(100, 0)
    assert resultado == 100


def test_desconto_cem():
    resultado = aplicar_desconto(100, 100)
    assert resultado == 0


def test_desconto_invalido():
    with pytest.raises(ValueError):
        aplicar_desconto(100, 110)


# ==========================================
# QUESTÃO 6 - MÉDIA
# ==========================================

def test_media_notas_diferentes():
    resultado = calcular_media([5, 7, 9])
    assert resultado == 7


def test_media_notas_iguais():
    resultado = calcular_media([8, 8, 8])
    assert resultado == 8


def test_media_uma_nota():
    resultado = calcular_media([10])
    assert resultado == 10


def test_media_lista_vazia():
    with pytest.raises(ValueError):
        calcular_media([])


