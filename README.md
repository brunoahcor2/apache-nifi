# apache-nifi

## Roteiro de instalação do Apache Nifi em um ambiente Unix.
* **Criado por:** Bruno Rocha
* **Ultima atualização:** 09.08.2023

## Instalando o JDK8
Estou realizando a instalação em um ambiente Linux (Ubuntu 20.04 LTS):

**Step 1: Update the apt repository**<br>
```
sudo apt update
```
**Step 2: Install Java 8 on Ubuntu**<br>
```
sudo apt install openjdk-8-jdk
```
**Step 3: Check the Java version on Ubuntu**<br>
```
java -version
```
**Step 3: Console output**<br>
```
openjdk version "1.8.0_382"
OpenJDK Runtime Environment (build 1.8.0_382-8u382-ga-1~20.04.1-b05)
OpenJDK 64-Bit Server VM (build 25.382-b05, mixed mode)
```
**Step 4: Configure JAVA_HOME in Ubuntu**<br>
```
export JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:/bin/java::")
```
**Step 5: Verify JAVA_HOME path in Ubuntu**<br>
```
source ~/.bashrc
```
```
echo $JAVA_HOME
```
**Step 5: Console output**<br>
```
/usr/lib/jvm/java-8-openjdk-amd64/jre
```

## Baixando o Nifi:
Vamos fazer o download no link abaixo, o arquivo tem 1,3GB o que pode demorar de 10 a 15 min dependendo da internet:
```
wget https://archive.apache.org/dist/nifi/1.11.4/nifi-1.11.4-bin.tar.gz
```

## Descompactando o arquivo:
Agora com o Download feito vamos descompactar o Nifi.
```
tar zfxv nifi-1.11.4-bin.tar.gz
```

## Iniciando o Nifi:
Agora entramos dentro do diretório do Nifi e rodamos os script de inicialização do serviço:
```
cd nifi-1.11.4
bin/nifi.sh start
```
## Verificando o Start do serviço:
No mesmo diretório para verificar os logs posso rodar o comando abaixo:
```
tail -300f logs/nifi-app.log
```
Caso as mensagens apareçam assim:
```
2023-08-09 15:52:43,235 INFO [main] org.apache.nifi.web.server.JettyServer NiFi has started. The UI is available at the following URLs:
2023-08-09 15:52:43,235 INFO [main] org.apache.nifi.web.server.JettyServer http://192.168.0.38:8080/nifi
2023-08-09 15:52:43,235 INFO [main] org.apache.nifi.web.server.JettyServer http://172.17.0.1:8080/nifi
2023-08-09 15:52:43,235 INFO [main] org.apache.nifi.web.server.JettyServer http://127.0.0.1:8080/nifi
```
É sinal que o Nifi iniciou com sucesso e você pode validar colando o link abaixo no navegador:
```
http://localhost:8080/
```
Se tudo deu certo, você vai ver a tela abaixo:
[![](https://github.com/AnselmoBorges/udemy02/blob/master/passoapasso/nifi.png)
