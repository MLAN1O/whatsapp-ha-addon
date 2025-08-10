FROM ghcr.io/hassio-addons/debian-base:7.8.3  
  
#install node 18 and npm  
RUN apt-get update && apt-get install -y curl gnupg2 && curl -sL https://deb.nodesource.com/setup_18.x | bash - && apt-get install -y nodejs git && \  
    apt-get update && apt-get install -y ffmpeg git libnss3 libatk-bridge2.0-0 libxkbcommon-x11-0 libgbm-dev libasound2 chromium && \  
    rm -rf /var/lib/apt/lists/*  
  
# Configurar Puppeteer para usar Chromium do sistema  
ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true  
ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium  
  
# Copy root filesystem  
COPY rootfs /  
  
WORKDIR /app  
  
RUN git clone --branch "main" --depth=1 \  
        "https://github.com/MLAN1O/ha-whatsapp-web-rest-api.git" /app  
  
# install production dependencies  
RUN npm install  
  
RUN npm run build