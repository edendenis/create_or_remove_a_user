# Como configurar/instalar/usar `criar ou remover um novo usuáro` no `Linux Ubuntu`

## Resumo

Neste documento estão contidos os principais comandos e configurações para configurar/instalar/usar `criar ou remover um novo usuáro` no `Linux Ubuntu`.

## _Abstract_

_This document contains the main commands and settings to configure/install/use `create or remove a new user` in `Linux Ubuntu`._


## Descrição [2]

### `Usuário`

Um "usuário" em tecnologia da informação se refere a uma entidade que interage com um sistema de computador, software ou serviço online. Cada usuário geralmente tem sua própria identidade, autenticada por meio de credenciais como nome de usuário e senha. Os usuários podem acessar recursos, armazenar dados, executar programas e realizar uma variedade de outras ações, dependendo das permissões e do papel atribuídos a eles dentro do sistema. Gerenciar usuários é uma parte fundamental da administração de sistemas de TI, garantindo a segurança, a privacidade e a eficiência do ambiente computacional.


## 1. Como configurar/instalar/usar `criar ou remover um novo usuáro` no `Linux Ubuntu` [1]

Para configurar/instalar/usar o `criar ou remover um novo usuáro` no `Linux Ubuntu`, você pode seguir estes passos:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes APT. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo APT e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando: `sudo apt clean` 
    
    2.2 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: `sudo apt update -y`

    2.5 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:  `sudo apt list --upgradable`

    2.6 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update -y`. Digite o seguinte comando e pressione `Enter`: `sudo apt full-upgrade -y`

    2.7 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.8 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

## 1.1 Criar um novo usuário

Para criar um novo usuário no Linux Ubuntu e configurá-lo adequadamente, você pode seguir os passos abaixo. Esses passos incluem a criação do usuário, definição de senha, concessão de permissões para utilizar o sudo e definição de permissões para acessar pastas específicas.

1. **Criar um Novo Usuário:** Abra um terminal e utilize o comando adduser para criar um novo usuário. Por exemplo, para criar um usuário chamado novousuario, você deve executar: `sudo adduser novousuario`

    Você será solicitado a inserir e confirmar uma senha para o novo usuário e, opcionalmente, preencher algumas informações adicionais. Após completar essas etapas, o usuário será criado.

2. **Conceder Permissões do `sudo`:** Para que o novo usuário possa executar comandos como superusuário, você precisa adicionar o usuário ao grupo `sudo`. Use o comando: `sudo usermod -aG sudo novousuario`

    Esse comando modifica o usuário `novousuario`, adicionando-o ao grupo `sudo`, o que concede permissões para executar comandos como superusuário.

3. **Definir Permissões de Acesso a Pastas:** Se você quiser que o novo usuário tenha acesso a pastas específicas, pode alterar as permissões dessas pastas usando o comando `chmod` ou `chown`. Por exemplo, se você quiser que novousuario tenha acesso à pasta `/dados`, você pode mudar o proprietário da pasta para novousuario: `sudo chown -R novousuario:novousuario /dados`

    Ou, se você quiser apenas conceder permissões de leitura e execução para o usuário em uma pasta específica: `sudo chmod -R 755 /dados`

4. **Outras Configurações: **Dependendo do que o novo usuário precisará fazer, você pode precisar realizar configurações adicionais, como definir variáveis de ambiente, configurar cron jobs, ou instalar softwares específicos para esse usuário.

Após seguir estes passos, o novousuario estará configurado no Ubuntu com acesso básico, permissões de sudo e acesso às pastas especificadas.

### 1.1.1 Adicionar permissões ao usuário

Para adicionar essas permissões a um usuário no ambiente de linha de comando, você teria que realizar várias tarefas diferentes, algumas das quais são gerenciadas automaticamente pelo sistema e outras que podem exigir a adição do usuário a grupos específicos do sistema.

1. **Acesso a dispositivos de armazenamento externos automaticamente:** Normalmente, o sistema gerencia essas permissões automaticamente quando você conecta um dispositivo. Para garantir isso, o usuário deve ser parte do grupo plugdev: `sudo usermod -a -G plugdev edenedfsls`

2. **Configurar impressoras:** O usuário precisa ser adicionado ao grupo `lpadmin`: `sudo usermod -a -G lpadmin edenedfsls`

3. **Conectar à Internet usando um modem:** Isso geralmente é permitido para todos os usuários por padrão: **NÃO** é necessário executar comando.

4. **Conectar a redes sem fio e ethernet:** Isso também é permitido por padrão para todos os usuários: **NÃO** é necessário executar comando.

5. **Monitorar logs do sistema:** Para visualizar muitos logs do sistema, o usuário precisa ter permissões de leitura nos arquivos de log, que geralmente estão localizados em `/var/log`. Alguns desses arquivos são acessíveis apenas pelo superusuário: `sudo usermod -a -G adm edenedfsls`

6. **Enviar e receber faxes:** Isso dependeria do software específico usado para gerenciar faxes: **NÃO** é necessário executar comando.

7. **Compartilhar arquivos com a rede local:** O compartilhamento de arquivos é geralmente gerenciado por serviços como `Samba`, e você configuraria as permissões no próprio serviço: Para compartilhar arquivos com o serviço Samba, você configuraria as permissões no arquivo de configuração do Samba (`smb.conf`) e não através de comandos de terminal para grupos de usuários.

8. **Uso de dispositivos de áudio:** Normalmente é permitido por padrão: `sudo usermod -a -G audio edenedfsls`

9. **Uso de drives de CD-ROM:** Permissão padrão na maioria dos casos: ``sudo usermod -a -G cdrom edenedfsls`

10. **Uso de disquetes:** Se ainda for necessário, o usuário precisa ter acesso ao dispositivo de disquete, mas é incomum nos sistemas modernos: `sudo usermod -a -G floppy edenedfsls`

11. **Uso de modems, scanners, drives de fita, dispositivos de vídeo:** O usuário precisaria ser adicionado aos grupos específicos que têm permissão para acessar esses dispositivos: `sudo usermod -a -G scanner edenedfsls`

    Nem todas essas permissões são necessárias para todos os usuários. Por exemplo, o uso de drives de disquete é obsoleto, e enviar e receber faxes pode não ser necessário se o usuário não trabalhar com faxes.

12. **Verificar os grupos existentes em seu sistema:** Para verificar os grupos existentes em seu sistema e a qual grupo um usuário pertence, você pode usar os comandos `groups` e `cat /etc/group`, respectivamente.

Por fim, as permissões devem ser concedidas com base nas necessidades específicas do usuário e na política de segurança da organização ou do administrador do sistema. Além disso, o ambiente gráfico pode ter uma ferramenta de gerenciamento de usuários que simplifica esse processo, permitindo ajustar essas configurações com cliques em vez de comandos de terminal.

## 1.2 Remover um usuário

1. Para remover um usuário, você pode usar o comando `deluser`. Por exemplo, para remover um usuário chamado novousuario, execute: `sudo deluser novousuario`

    1.1 Este comando remove o usuário, mas mantém sua pasta `home` e `e-mails`. Se você também quiser remover a pasta `home` e `e-mail` do usuário, precisa adicionar a opção `--remove-home`: `sudo deluser --remove-home novousuario`

2. **Remover o Usuário do Grupo `sudo` (se necessário):** Se você também quiser garantir que o usuário seja removido do grupo `sudo`, normalmente, o `deluser` já cuida disso. No entanto, se quiser verificar manualmente se o usuário ainda está em algum grupo, você pode inspecionar o arquivo `/etc/group`. Para remover o usuário de um grupo específico manualmente, você poderia usar o `gpasswd` ou editar o arquivo `/etc/group` diretamente, mas essa etapa normalmente não é necessária se você estiver usando deluser corretamente.

3. **Verificar se o Usuário Foi Removido:** Após a remoção, você pode querer confirmar que o usuário foi realmente excluído. Para verificar se o usuário ainda existe, você pode procurar pelo nome dele nos arquivos do sistema: `cat /etc/passwd`

    Este comando lista todos os usuários no sistema. Se `novousuario` foi removido, ele não deve aparecer na lista.

4. **Limpeza Adicional (se necessário):** Se houver arquivos em outros locais do sistema que pertenciam ao usuário removido, você pode querer localizá-los e removê-los manualmente. Isso pode ser necessário se o usuário tinha permissões de acesso a diretórios específicos fora de sua pasta `home`.

Ao seguir esses passos, você remove um usuário e sua pasta `home` no Ubuntu, garantindo que ele não tenha mais acesso ao sistema e que seus dados pessoais não permaneçam no servidor ou máquina.

## 2. Código completo para configurar/instalar/usar

Para configurar/instalar/usar o `criar ou remover um novo usuário` no `Linux Ubuntu`sem precisar digitar linha por linha, você pode seguir estas etapas:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Digite o seguinte comando e pressione `Enter`:

    ```
    NÃO há.
    ```


## Referências

[3] OPENAI. ***Novo Usuário Com Permissões.*** Disponível em: <https://chat.openai.com/c/b641df71-d442-4ced-b269-e24929a2a8c2> (texto adaptado). Acessado em: 10/03/2024 13:47.

[2] OPENAI. ***Vs code: editor popular.*** Disponível em: <https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42> (texto adaptado). Acessado em: 10/03/2024 13:48.


