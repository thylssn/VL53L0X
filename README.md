# Sensor de Distância a Laser VL53L0X com Raspberry Pi Pico

Este repositório contém um projeto em C para utilizar o sensor de distância a laser Time-of-Flight (ToF) VL53L0X com a placa Raspberry Pi Pico.

## ✨ Funcionalidades

-   Integração com o sensor de distância a laser VL53L0X.
-   Leitura contínua da distância em milímetros.
-   Comunicação via I2C com a Raspberry Pi Pico.
-   Projeto configurado para fácil compilação com o SDK do Raspberry Pi Pico e CMake.

## 🛠️ Hardware Necessário

-   **Raspberry Pi Pico** ou **Pico W**
-   **Sensor de Distância a Laser VL53L0X**
-   **Cabos/Jumpers** para conexão

## 📦 Software e Dependências

-   **Visual Studio Code**
-   **Extensão Raspberry Pi Pico/W para VS Code**
-   **Raspberry Pi Pico SDK**, **ARM GCC Compiler** e **CMake**

## 🔌 Conexões

Conecte o sensor VL53L0X à Raspberry Pi Pico utilizando a interface I2C0, conforme definido no arquivo `src/sensor-distancia-laser.c`:

| Pino do VL53L0X | Pino da Raspberry Pi Pico | Descrição        |
| :-------------- | :------------------------ | :--------------- |
| **VIN** | **3V3 (OUT)**   | Alimentação      |
| **GND** | **GND**        | Terra            |
| **SCL** | **GP1 (I2C0 SCL)**  | Clock do I2C     |
| **SDA** | **GP0 (I2C0 SDA)** | Dados do I2C     |

## 🚀 Como Compilar e Executar

### Usando o VS Code com a Extensão Raspberry Pi Pico (Recomendado)

Este projeto já está configurado para a extensão oficial, tornando o processo muito simples.

1.  **Abra o Projeto:** Abra a pasta raiz do projeto no Visual Studio Code.
2.  **Prepare a Placa:** Coloque a Raspberry Pi Pico em modo **BOOTSEL** (pressione e segure o botão BOOTSEL enquanto conecta o cabo USB).
3.  **Envie o Código:** Clique no botão **`Run`** na barra de status ou use o atalho. A extensão irá compilar o código e enviá-lo automaticamente para a placa usando o `picotool`.
6.  **Visualize a Saída:** Abra o monitor serial integrado do VS Code para ver as medições de distância.

### Usando a Linha de Comando

Se preferir não usar o VS Code, você pode compilar manualmente.

1.  **Clone o repositório:**
    ```bash
    git clone <URL_DO_SEU_REPOSITORIO>
    cd <NOME_DA_PASTA>
    ```
2.  **Crie e configure o build:**
    * Certifique-se de que a variável de ambiente `PICO_SDK_PATH` aponta para o diretório do seu SDK.
    ```bash
    mkdir build
    cd build
    cmake ..
    ```
3.  **Compile:**
    ```bash
    make
    ```
4.  **Carregue o firmware (`.uf2`):**
    -   Coloque a Pico em modo **BOOTSEL**.
    -   Copie o arquivo `build/sensor-distancia-laser.uf2` para o drive que a Pico montou no seu sistema.

## 📂 Estrutura do Projeto

```
.
├── .vscode/               # Arquivos de configuração do Visual Studio Code para a extensão
├── build/                 # Diretório (ignorado) onde os arquivos de compilação são gerados
├── inc/                   # Arquivos de cabeçalho (.h)
│   └── tof.h
├── src/                   # Arquivos de código-fonte (.c)
│   ├── sensor-distancia-laser.c
│   └── tof.c
├── .gitignore             # Arquivos e pastas ignorados pelo Git
├── CMakeLists.txt         # Arquivo de configuração do CMake para o projeto
├── LICENSE                # Licença do projeto
└── pico_sdk_import.cmake  # Script para importar o SDK do Pico
```

## 👨‍💻 Autores

-   **thalyssonDEV**
## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
