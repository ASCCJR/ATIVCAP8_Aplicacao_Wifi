# ATIVCAP8_Aplicacao_Wifi

# Servidor HTTP com Controle de LED via Access Point (Raspberry Pi Pico W)

## 📌 Visão Geral
Este projeto implementa um servidor HTTP embarcado no Raspberry Pi Pico W, que funciona como um Access Point Wi-Fi para controle remoto de um LED e buzzer. O sistema inclui:
- Interface web para ativar/desativar modo de emergência
- LED e buzzer intermitentes no modo emergência
- Display OLED para feedback visual
- Desligamento seguro via tecla 'd'

## 🛠️ Hardware Necessário
- Raspberry Pi Pico W
- LED (conectado ao GPIO 13)
- Buzzer ativo (conectado ao GPIO 21)
- Display OLED SSD1306 (conectado via I2C - GPIO 14/15)
- Resistores apropriados para LED/buzzer

## 🔌 Configuração de Pinagem
| Componente | Pino GPIO |
|------------|----------|
| LED        | 13       |
| Buzzer     | 21       |
| OLED SDA   | 14       |
| OLED SCL   | 15       |

## ⚙️ Funcionalidades
1. **Access Point Wi-Fi**:
   - SSID: `picow_test`
   - Senha: `password`
   - IP do servidor: `192.168.4.1`

2. **Interface Web**:
   - Acessível em `http://192.168.4.1/ledtest`
   - Botões para ligar/desligar o modo emergência

3. **Indicadores**:
   - LED vermelho piscante no modo emergência
   - Buzzer com sinal sonoro intermitente
   - Mensagens no display OLED ("EVACUAR" ou "Sistema em repouso")

4. **Controle**:
   - Tecla 'd' no terminal para desligar o Access Point

## 🚀 Como Usar
1. Conecte o hardware conforme a pinagem especificada
2. Compile e carregue o firmware no Pico W
3. Conecte-se à rede `picow_test` (senha: `password`)
4. Acesse `http://192.168.4.1/ledtest` no navegador
5. Use os botões para controlar o modo emergência

## 🧩 Estrutura do Código
```
├── Definições de pinos e constantes
├── Variáveis de controle
├── Funções auxiliares (OLED, buzzer, LED)
├── Servidor HTTP (TCP/IP)
├── Função principal (inicialização e loop)
```

## 📝 Notas de Desenvolvimento
- O buzzer opera em 2kHz com duty cycle de 50%
- O LED pisca em intervalos de 300ms no modo emergência
- O sistema usa LWIP para stack TCP/IP
- O display OLED é atualizado via I2C a 400kHz

## 💡 Melhorias Futuras
- Adicionar temporizador para desligamento automático do buzzer
- Implementar página web com CSS melhorado
- Adicionar autenticação básica na interface web
- Suporte para configuração via web (SSID/senha)

## ⚠️ Limitações Conhecidas
- Suporta apenas um cliente HTTP por vez
- Não possui tratamento avançado de erros de conexão
- Interface web básica sem persistência de estado

## Propósito

Este projeto foi desenvolvido com fins estritamente educacionais e para aprendizagem durante a residência em sistemas embarcados pelo Embarcatech. O objetivo principal é demonstrar a integração de múltiplos periféricos (Wi-Fi, GPIO, I2C) em um sistema embarcado, implementando protocolos de rede e interfaces de usuário simples. Não se destina a uso em ambientes de produção ou sistemas críticos.
