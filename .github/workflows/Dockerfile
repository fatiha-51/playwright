# 1. On part de l’image officielle Playwright qui contient Node.js + navigateurs + dépendances système
FROM mcr.microsoft.com/playwright:latest               # version la plus récente inclut Chromium, Firefox, WebKit et libs système :contentReference[oaicite:0]{index=0}

# 2. Création et passage dans le répertoire de l’application
WORKDIR /app

# 3. Copie des fichiers de dépendances pour activer le cache Docker
COPY package*.json ./

# 4. Installation des dépendances npm
RUN npm ci                                              # installe strictement ce qui est dans package-lock.json :contentReference[oaicite:1]{index=1}

# 5. (Optionnel) Réinstallation des navigateurs si nécessaire
# RUN npx playwright install --with-deps               # utile si vous ne partez pas de l’image officielle “noble” :contentReference[oaicite:2]{index=2}

# 6. Copie du reste de votre code source
COPY . .

# 7. Commande par défaut pour exécuter vos tests Playwright
CMD ["npx", "playwright", "test"]
