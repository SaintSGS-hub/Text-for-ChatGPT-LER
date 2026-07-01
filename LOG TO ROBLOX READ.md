📄 RELATO TÉCNICO – CRASH ROBLOX (zdev-recover / input freeze / shutdown delay)

Sistema operacional: Windows 11 Pro 23H2 (Build 22631.6199)
GPU: NVIDIA RTX 3060 (Driver 610.62)
Instalação Roblox: teste via instalador oficial e Microsoft Store
Ambiente adicional: testes também realizados com Fishstrap (launcher alternativo)

🧩 Descrição do problema

O Roblox apresenta falhas consistentes de estabilidade após alguns minutos de gameplay (entre ~40 segundos e ~10 minutos dependendo da sessão).

O comportamento observado é:

O jogo roda normalmente inicialmente
Após tempo variável, ocorre freeze completo de input
Personagem para de responder (teclado e mouse deixam de funcionar dentro do jogo)
O jogo ainda continua renderizando parcialmente
Após aproximadamente 2–3 minutos, o processo encerra automaticamente
O Windows exibe “programa não está respondendo”
⏱️ Frequência e consistência

O problema ocorre:

Em qualquer mapa ou servidor
Com conta nova e conta principal
Após reinstalação limpa do Roblox
Em diferentes sessões consecutivas
Com variação de tempo consistente (curto intervalo até falha)
📜 Evidências de logs do cliente

Nos logs do Roblox foi identificado:

Canal ativo:

RobloxChannel has been set to zdev-recover-725-t1

Uso de bucket experimental/recovery:

settingsUrl:
https://clientsettingscdn.roblox.com/.../bucket/zdev-recover-725-t1/

Sistema de cache persistente de flags:

[FlagCache] Loading flags from local cache
[TombstoneCache] channel 'zdev-recover-725-t1'

Persistência de estado (tombstone cache):

read from file: ...\Temp\Roblox\cache\tombstone.dat
🔎 Tentativas de resolução já realizadas
Reinstalação completa do Roblox (site oficial e Microsoft Store)
Teste com conta nova
Teste com diferentes servidores e mapas
Criação de novo usuário no Windows
Limpeza parcial de cache do Roblox
Desativação de softwares em segundo plano (Rapoo macro software, Edge Game Assist)
Testes com Fishstrap launcher (mesmo comportamento observado)
Testes com dumps e ProcDump (sem sucesso devido ao encerramento do processo durante captura)
🧪 Resultado

O comportamento sugere que o cliente Roblox está sendo executado em canal experimental/recovery (zdev-recover-725-t1) com possível associação persistente via cache de flags (tombstone system), resultando em instabilidade grave de input e encerramento do processo após alguns minutos.

❗ Solicitação

Solicito verificação de:

Atribuição incorreta de bucket experimental (zdev-recover)
Reset de experiment flags / holdout assignment
Correção de canal de distribuição do cliente
Validação de integridade do clientsettings CDN assignment
Possível desassociação de A/B testing bucket persistente
