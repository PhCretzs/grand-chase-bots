# 🎮 grand-chase-bots

Coleção de scripts de automação para o jogo Grand Chase, desenvolvidos ao longo da graduação em Engenharia de Computação. O repositório documenta a evolução do código desde os primeiros experimentos até implementações com visão computacional.

---

## 📁 Estrutura do Repositório

```
grand-chase-bots/
│
├── vision-bot/                  # Bot com visão computacional (projeto mais recente)
│   ├── main.py                  # Loop principal e lógica de decisão
│   ├── imagerecognition.py      # Detecção de player e monstros via OpenCV
│   └── windowcapture.py         # Captura de janela com MSS + Win32GUI
│
├── presence-bot/                # Bot de marcação de presença (GC Diário)
│   ├── gc_presence.py           # Versão atual — usa detecção de imagem com PyAutoGUI
│   └── legacy/
│       └── PresençaGC_old.py    # Versão original — coordenadas hardcoded, sem funções
│
└── autopet/                     # Bot de coleta automática de pet
    ├── autopet.py               # Detecta vida na tela e pressiona tecla
    └── autopet_v2.py            # (em desenvolvimento)
```

---

## 🤖 Projetos

### vision-bot

<video src="https://github.com/PhCretzs/grand-chase-bots/raw/refs/heads/main/teste%20bot.mp4" width="100%" controls></video>

O projeto mais recente e técnico da coleção. Captura a tela do jogo em tempo real e usa OpenCV para identificar o personagem (pixel vermelho `#FF0000`) e monstros (pixel amarelo `#FFD200`) por detecção de cor. Um loop principal roda a captura e reconhecimento, enquanto uma thread separada executa os comandos de teclado baseada nas posições detectadas.

**Principais tecnologias:** `opencv-python`, `mss`, `pywin32`, `threading`, `pynput`

---

### presence-bot
Automatiza a marcação de presença diária em múltiplos personagens. A versão atual (`gc_presence.py`) usa `pyautogui.locateOnScreen` para identificar elementos da UI dinamicamente, adaptando-se à posição real dos ícones na tela. 

A versão legada (`PresençaGC_old.py`) foi o ponto de partida: ~300 linhas com coordenadas absolutas hardcoded e código duplicado — mantida no repositório para ilustrar a evolução do projeto.

**Principais tecnologias:** `pyautogui`, `pywin32`, `keyboard`

---

### autopet
Script simples que monitora a tela em busca de um indicador de vida e pressiona uma tecla automaticamente quando detectado. Primeiro experimento com automação de entrada.

**Principais tecnologias:** `pyautogui`, `keyboard`, `pynput`

---

## 📈 Evolução

| Versão | Abordagem | Limitação |
|---|---|---|
| `PresençaGC_old.py` | Coordenadas absolutas, sem funções | Quebra com qualquer mudança de resolução |
| `gc_presence.py` | Detecção de imagem com PyAutoGUI | Dependente de screenshots de referência |
| `vision-bot` | OpenCV + threading | Detecção de cor exata, sensível a variações |

---

## ⚙️ Requisitos

```
opencv-python
numpy
pyautogui
pywin32
mss
keyboard
pynput
```

Instale com:
```bash
pip install opencv-python numpy pyautogui pywin32 mss keyboard pynput
```

> ⚠️ Os scripts foram desenvolvidos para Windows e dependem de APIs Win32. Caminhos de imagens de referência precisam ser ajustados para o ambiente local.

---

## 📝 Notas

Este repositório é um projeto pessoal de aprendizado desenvolvido durante a graduação. Os scripts foram escritos para uso próprio e ilustram a progressão do desenvolvimento — do código procedural básico até o uso de visão computacional com threading.

