# YouTube Video Downloader

## 📌 Sobre o Projeto
Este projeto surgiu da necessidade de baixar um vídeo do YouTube. Durante a pesquisa por sites gratuitos para essa tarefa, percebi que muitos exigiam pagamento ou estavam cheios de anúncios e restrições. Para contornar essa limitação, desenvolvi este script em Python no Google Colab para baixar vídeos diretamente do YouTube de forma simples e eficiente.

## 🚀 Tecnologias Utilizadas
- **Python** 🐍
- **yt-dlp** (um fork avançado do youtube-dl para download de vídeos)
- **Google Colab** (ambiente de desenvolvimento utilizado)

## 🛠️ Como Funciona
O script utiliza a biblioteca `yt-dlp` para baixar vídeos do YouTube com a melhor qualidade disponível até 4K.

## 📥 Instalação e Uso
### 1️⃣ Instalar a biblioteca necessária
No Google Colab, execute o seguinte comando para instalar o `yt-dlp`:
```python
!pip install yt-dlp
```

### 2️⃣ Código do Script
Copie e execute o código abaixo no Google Colab:
```python
import yt_dlp
import os

def download_youtube_video(url):
    try:
        output_path = os.path.join(os.getcwd(), "Downloads")
        os.makedirs(output_path, exist_ok=True)

        ydl_opts = {
            'format': 'bestvideo[height<=2160]+bestaudio/best',  # Força qualidade até 4K
            'outtmpl': os.path.join(output_path, '%(title)s.%(ext)s'),
        }

        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            print(f"Iniciando o download do vídeo: {url}")
            ydl.download([url])

        print(f"Download concluído! Salvo em {output_path}")

    except Exception as e:
        print(f"Erro durante o download: {e}")

if __name__ == "__main__":
    video_url = input("Digite a URL do vídeo do YouTube: ")
    if video_url.strip():
        download_youtube_video(video_url)
    else:
        print("A URL fornecida é inválida.")
```

### 3️⃣ Executando o Script
- Insira a URL do vídeo do YouTube quando solicitado.
- O vídeo será baixado e salvo na pasta `Downloads` dentro do diretório de trabalho do Colab.
- Você pode acessar o vídeo baixado navegando até a pasta correspondente.

## 📝 Notas
- Este script funciona apenas em vídeos públicos ou não listados do YouTube.
- Caso encontre problemas, certifique-se de que `yt-dlp` está atualizado com o comando:
  ```python
  !pip install --upgrade yt-dlp
  ```

## 🔗 Referências
- [yt-dlp no GitHub](https://github.com/yt-dlp/yt-dlp)

---

Agora você pode baixar vídeos do YouTube sem complicações! 🚀
