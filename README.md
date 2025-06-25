def VER_TODAS_DOACOES():
    print(f'{CIANO_CLARO}--- LISTA DE TODAS AS DOAÇÕES ---  {RESET}')
    if not DOACOES:
        print(f'{VERMELHO_CLARO}NENHUMA DOAÇÃO REGISTRADA.{RESET}')
        return
    for D in DOACOES:
        print(f"{AZUL_CLARO}ID: {D['id']} | DOADOR: {D['doador']} | TIPO: {D['tipo']} | QTD: {D['quantidade']} | DATA: {D['data']} | ENTREGUE: {'SIM' if D['entregue'] else 'NÃO'}{RESET}")
        print('\n')



def CONSULTAR_POR_TIPO():
        tipo = input('TIPO DE DOAÇÃO: ').strip().lower()
        encontrou = False
        for d in DOACOES:
            if d['tipo'].strip().lower() == tipo:
                print(
                    f"ID: {d['id']} | DOADOR: {d['doador']} | QTD: {d['quantidade']} | DATA: {d['data']} | ENTREGUE: {'SIM' if d['entregue'] else 'NÃO'}")
                encontrou = True
        if not encontrou: print(f'NENHUMA DOAÇÃO DO TIPO "{tipo.upper()}" ENCONTRADA.')


def MARCAR_COMO_ENTREGUE():
    print(f'{CIANO_CLARO}--- MARCAR DOAÇÃO COMO ENTREGUE ---{RESET}')
    try:
        ID_BUSCA = int(input(f'{AZUL_CLARO}DIGITE O ID DA DOAÇÃO QUE FOI ENTREGUE: '))
        for D in DOACOES:
            if D[f'id'] == ID_BUSCA:
                D[f'entregue{RESET}'] = True
                print(f'{AMARELO_CLARO}✅ DOAÇÃO MARCADA COMO ENTREGUE!{RESET}')
                print('\n')
                return
        print(f'{VERMELHO_CLARO}ID NÃO ENCONTRADO.')
        print('\n')
    except ValueError:
        print(f'ID INVÁLIDO.{RESET}')



def MENU():
    while True:
        print(f'{CIANO_CLARO}===== SISTEMA DE GERENCIAMENTO DE DOAÇÕES ====={RESET}')
        print(f'{AZUL_CLARO}1. REGISTRAR DOAÇÃO')
        print(f'2. VER TODAS DOAÇÕES ')
        print(f'3. CONSULTAR POR TIPO')
        print(f'4. MARCAR COMO ENTREGUE{RESET}')
        print(f'{VERMELHO_CLARO}5. SAIR{RESET}')
        ESCOLHA = str(input(f'{CIANO_CLARO} ESCOLHA UMA OPÇAO: {RESET}'))
        print('\n')
        if ESCOLHA == '1':
            REGISTRAR_DOACAO()
        elif ESCOLHA == '2':
            VER_TODAS_DOACOES()
        elif ESCOLHA == '3':
            CONSULTAR_POR_TIPO()
        elif ESCOLHA == '4':
            MARCAR_COMO_ENTREGUE()
        elif ESCOLHA == '5':

            break
        else:
            print(f'{VERMELHO_CLARO}❌OPÇÃO INVALIDA TENTA NOVAMENTE🥵😒.{RESET}')


MENU()
