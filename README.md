# protheus-prequisitos
## Pré-Requisitos Sistêmicos

[![LinkedIn](https://cdn3.iconfinder.com/data/icons/socialnetworking/32/linkedin.png?style=social)](https://www.linkedin.com/in/abrha%C3%A3o-ribeiro-2b019225?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3BzcrC%2FntDQB%2BXZFr3N8PzBg%3D%3D)



## Propósito

Verificar se os pré-requisitos sistêmicos são atendidos para não gerar uma interrupção abrupta do programa (error.log)

O programa verifica a existência de programas no repositório e também se determinados campos existem.
OBs: para esta versão ainda, é necessário que pelo menos a tabela exista


#### Utilização

O exemplo abaixo verifica se o programa OxMessage (PRW ou TLPP) está compilado no repositório, e se ele possui data mínimia de 18/11/2020.
Também reliza a verificação da existência dos campos ZL0_FORNEC e ZL0_TICK.

``` bash
User Function Exemplo()    
    
    /** Realiza a verificacao de todos os pre-requisitos para funcionamento do programa **/
    ChkFile("ZL0")
    DbSelectArea("ZL0")    
    xoPreRequisitos := OxPreRequisitos():Create()
    xoPreRequisitos:ExigeFonte ( {"OXMESSAGE": "18/11/2020"} )
    xoPreRequisitos:ExigeCampo ( {"ZL0": {"ZL0_FORNEC","ZL0_TICK"} } )
    ZL0->(DbCloseArea())
    If !xoPreRequisitos:Atende()
        Return .F.
    EndIf
    /****************************************************************************************/

Return .T.
```

Caso o ambiente não atenda aos pré-requisitos estabelecidos como importantes para o funcionamento da rotina, será disparada mensagem de erro.

![Template](https://raw.githubusercontent.com/abrhaao/protheus-prequisitos/master/validacoes.png)

![Template](https://raw.githubusercontent.com/abrhaao/protheus-prequisitos/master/validacoes-soft.png)
