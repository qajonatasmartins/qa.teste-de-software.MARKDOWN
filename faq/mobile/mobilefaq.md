# FAQ Mobile

## Como obter o package e activity de um aplicativo para automação mobile

### Objetivo

Ajudar na obtenção do package e activity para conectar o framework de teste com o aplicativo a ser automatizado.

### Pré-requisitos

- Necessário que o adb esteja instalado na máquina;
- Certifique-se de ter o aplicativo instalado no dispositivo móvel ou no emulador que você está usando para testes.

### Passo a passo

1. Abra o terminal
2. Navegue até o diretório onde você tem as ferramentas de desenvolvimento Android instaladas. Normalmente, o diretório é algo como `android-sdk/platform-tools/`.
3. Execute o seguinte comando para listar todos os pacotes instalados no dispositivo móvel ou no emulador: `adb shell pm list packages`
   - Isso mostrará uma lista de todos os pacotes instalados. Procure o pacote do aplicativo específico que você deseja testar. O nome do pacote geralmente segue o formato "com.example.app".
4. Depois de identificar o pacote do aplicativo, execute o seguinte comando para obter a lista de activities no pacote: `adb shell dumpsys package <nome_do_pacote> | grep -E 'Activity'`
    - Substitua <nome_do_pacote> pelo nome do pacote que você encontrou no passo anterior. Esse comando filtrará a saída para exibir apenas as linhas que contenham "Activity" e mostrará os nomes das activities do aplicativo.
    - Por exemplo, se o pacote do aplicativo for "com.example.app", o comando ficaria assim:  `adb shell dumpsys package com.example.app | grep -E 'Activity'`
6. Analise a saída do comando e procure pela activity que você deseja automatizar. Normalmente, as activities têm nomes como "com.example.app.MainActivity".

Referências
- [Android Debug Bridge (adb)](https://developer.android.com/tools/adb)
- [adbshell](https://adbshell.com/commands)
