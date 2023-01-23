![Grasscutter](https://socialify.git.ci/Grasscutters/Grasscutter/image?description=1&forks=1&issues=1&language=1&logo=https%3A%2F%2Fs2.loli.net%2F2022%2F04%2F25%2FxOiJn7lCdcT5Mw1.png&name=1&owner=1&pulls=1&stargazers=1&theme=Light)
<div align="center"><img alt="Documentation" src="https://img.shields.io/badge/Wiki-Grasscutter-blue?style=for-the-badge&link=https://github.com/Grasscutters/Grasscutter/wiki&link=https://github.com/Grasscutters/Grasscutter/wiki"> <img alt="GitHub release (latest by date)" src="https://img.shields.io/github/v/release/Grasscutters/Grasscutter?logo=java&style=for-the-badge"> <img alt="GitHub" src="https://img.shields.io/github/license/Grasscutters/Grasscutter?style=for-the-badge"> <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/Grasscutters/Grasscutter?style=for-the-badge"> <img alt="GitHub Workflow Status" src="https://img.shields.io/github/workflow/status/Grasscutters/Grasscutter/Build?logo=github&style=for-the-badge"></div>

<div align="center"><a href="https://discord.gg/T5vZU6UyeG"><img alt="Discord - Grasscutter" src="https://img.shields.io/discord/965284035985305680?label=Discord&logo=discord&style=for-the-badge"></a></div>

[EN](README.md) | [简中](README_zh-CN.md) | [繁中](README_zh-TW.md) | [FR](README_fr-FR.md) | [ES](README_es-ES.md) | [HE](README_HE.md) | [RU](README_ru-RU.md) | [PL](README_pl-PL.md) | [ID](README_id-ID.md) | [KR](README_ko-KR.md) | [FIL/PH](README_fil-PH.md) | [NL](README_NL.md) | [JP](README_ja-JP.md) | [IT](README_it-IT.md)

**Atenção:** Nós sempre estamos de braços abertos e recebendo novos contribuidores. Mais antes de adicionar sua contribuição, por favor, leia nosso [Código de conduta](https://github.com/Grasscutters/Grasscutter/blob/stable/CONTRIBUTING.md).

## Funcionalidades atuais

* Sistema de Login
* Combate
* Lista de amigos
* Teleportes
* Sistema de obtenção de personagens (Gatcha)
* Co-op *parcialmente* funcionando
* Criar monstros via console
* Recursos de inventário (receber itens/bonecos, evoluir itens/bonecos, etc)

## Guia rápido de instalação

**Nota:** Para suporte, por favor entre em nosso [Discord](https://discord.gg/T5vZU6UyeG).

### Requesitos

* [Java SE - 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) ou mais atual

  **Nota:** Se você apenas deseja **rodar o servidor**, então apenas o **jre** já esta de bom tamanho.

* [MongoDB](https://www.mongodb.com/try/download/community) (recomendamos a v4.0+)

* Proxy Daemon: [mitmproxy](https://mitmproxy.org/) (mitmdump, recomendado), [Fiddler Classic](https://telerik-fiddler.s3.amazonaws.com/fiddler/FiddlerSetup.exe), etc.

### Iniciando

**Nota:** Se você estiver atualizando de uma versão antiga, delete o arquivo `config.json` para gerar um novo.

1. Obtendo o `grasscutter.jar`
   - Baixe de [lançamentos](https://github.com/Grasscutters/Grasscutter/releases/latest) ou [desenvolvimento](https://github.com/Grasscutters/Grasscutter/actions/workflows/build.yml) ou [compile você mesmo](#building).
2. Crie uma pasta com o nome `resources` na pasta aonde está o grasscutter.jar e mova os seguintes arquivos `BinOutput, ExcelBinOutput, Readables, Scripts, Subtitle, TextMap` para a pasta. *(Cheque a [wiki](https://github.com/Grasscutters/Grasscutter/wiki) para mais detalhes de como obter os mesmos.)*
3. Inicie o Grasscutter com o  comando `java -jar grasscutter.jar`. **Verifique que o serviço mongodb está iniciado corretamente.**

### Conectando com o cliente

½. Crie uma conta pelo console do servidor com o [comando](https://github.com/Grasscutters/Grasscutter/wiki/Commands#:~:text=account%20%3Ccreate|delete%3E%20%3Cusername%3E%20[UID]).

1. Redirecione o trafego: (escolha apenas um)
    - mitmdump: `mitmdump -s proxy.py -k`

        - Confie no certificado CA:

          - O certificado CA geralmente está armazenado em `%USERPROFILE%\.mitmproxy`, de um clique duplo em `mitmproxy-ca-cert.cer` para [instalar](https://docs.microsoft.com/en-us/skype-sdk/sdn/articles/installing-the-trusted-root-certificate#installing-a-trusted-root-certificate) ou...

          - Via linha de comando *(precisa de privilégios de administrador)*

             ```shell
             certutil -addstore root %USERPROFILE%\.mitmproxy\mitmproxy-ca-cert.cer
             ```

    - Fiddler Classic: Inicie o Fiddler Classic, habilite `Decrypt HTTPS traffic` em (Tools -> Options -> HTTPS) e troque a porta padrão em (Tools -> Options -> Connections) para qualquer uma que não seje `8888`, execute [este script](https://github.com/Grasscutters/Grasscutter/wiki/Resources#fiddler-classic-jscript) (copie e cole na guia `FiddlerScript`) e clique no botão `Save Script`.

    - [Arquivo HOSTS](https://github.com/Grasscutters/Grasscutter/wiki/Resources#hosts-file)

2. Configure sua network proxy para `127.0.0.1:8080` ou para o proxy que você especificou acima.

- Para mitmproxy: Depois de configurar seu proxy e instalar o certificado, cheque http://mitm.it/ para verificar se o trafego está passando pelo mesmo.

**Você também poderá usar `start.cmd` para iniciar o proxy e o daemon automaticamente, mais você terá que setar a variável `JAVA_HOME` e configurar o arquivo `start_config.cmd`.**

### Criando uma compilação sua do servidor

Grasscutter usa Gradle para gerir as dependencias de criação.

**Requesitos:**

- [Java SE Development Kits - 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) ou superior.
- [Git](https://git-scm.com/downloads)

##### Windows

```shell
git clone https://github.com/Grasscutters/Grasscutter.git
cd Grasscutter
.\gradlew.bat # Setting up environments
.\gradlew jar # Compile
```

##### Linux

```bash
git clone https://github.com/Grasscutters/Grasscutter.git
cd Grasscutter
chmod +x gradlew
./gradlew jar # Compile
```

Você poderá encontrar o jar na pasta de output da pasta que você colocou a compilação.

### Comandos do servidor foram movidos para a [wiki](https://github.com/Grasscutters/Grasscutter/wiki/Commands)!

# Ajuda rápida

* Se a compilação não for executada com exito, por favor cheque sua instalação do JDK  (Tenha certeza que seja um JDK 17 ou superior e que a variavel de ambiente esteja configurada corretamente).
* Meu cliente não conecta, não faz login, 4206, etc... - Provavelmente seu proxy é *o problema*. Se você estiver usando fiddler, troque a porta padrão para qualquer uma que não seja 8888.
* Inicie em sequëncia: MongoDB > Grasscutter > Proxy Daemon (mitmdump, fiddler, etc.) > Jogo
