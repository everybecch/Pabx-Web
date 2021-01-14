# Asterisk Dashboard PABX WEB

Fala meus queridos 

deixo aqui umprojetinho pbx web criação exclusão e edição de ramais direto do banco 

antes nescessario a instalação do asterisk v13 ao v16

configuração do dialplan, extension.conf

[default]
exten => _X.,1,Dial(SIP/class225/${EXTEN},20,Tt)

exten => _1XXX,2,Dial(SIP/${EXTEN})

same => n,Queue(0010)

same => n,Noop(CAUSA DA LIGAÇÃO => ${HANGUPCAUSE})

same => n,Noop(STATUS CALL => ${DIALSTATUS})

same => n,Goto(status-${HANGUPCAUSE})

same => n(status-1),agi(googletts.agi,"Esse numero não existe.")

same => n,Hangup()

same => n(status-17),agi(googletts.agi,"Hum... esse numero esta ocupado")

same => n,Hangup()

nescessario criação de parametros de fila(queue) queue.conf

[general]

persistentmembers = yes

autofill = yes

monitor-type = MixMonitor

keepstats = yes

autofill = yes

retry = 2

strategy = leastrecent

timeout = 10

music = default

eventmemberstatus = 1

eventwhencalled = 1

joinempty = strict

;leavewhenempty=no

maxlen = 0

wrapuptime = 0

ringuse = no

;monitor-join=yes

;monitor-format=wav

;monitor-type=MixMonitor

;dic-announce-frequency=60

;periodic-announce=calling

[0010]

;autofill=yes

retry=5

strategy=leastrecent

timeout=15

music=default

joinempty=strict

;leavewhenempty=no

maxlen=0

wrapuptime=0

ringinuse=yes

penaltymemberslimit=0

maxlen=0

memberdelay=0
----------------------------------------------//-------------------------------------------//--------------------------------------//-----------------------------
Inserir tabelas no banco. encontra-se na pasta (arquivos para subir no banco)

Dar start nos modulos odbc

instalar mariadb mysql 

ativar conexão manager do asterisk com db 

------------------------------//-----------------------------------------------//-----------------------------------------------------------//------------


obrigado espero a contribuição de todos 

by: Everton Santos | Asterisk Dev
