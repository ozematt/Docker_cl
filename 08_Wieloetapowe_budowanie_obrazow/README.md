![Coders-Lab-1920px-no-background](https://user-images.githubusercontent.com/30623667/104709394-2cabee80-571f-11eb-9518-ea6a794e558e.png)


# Optymalizacja obrazu z wykorzystaniem wieloetapowego budowania


#### Cel zadania:
Modyfikacja Dockerfile z zadania 1 o zaawansowane techniki, takie jak wieloetapowe budowanie, aby zoptymalizować rozmiar i bezpieczeństwo obrazu.

#### Krok po kroku:
1. **Modyfikuj Dockerfile:**
    - Utwórz nową wersję Dockerfile, która wykorzysta wieloetapowe budowanie:
      ```
      # Etap budowania
      FROM node:alpine as build
      WORKDIR /app
      COPY . .
      RUN npm install && npm run build
 
      # Etap produkcyjny
      FROM nginx:alpine
      COPY --from=build /app/build /usr/share/nginx/html
      ```
    - Zakładamy, że Twoja aplikacja jest aplikacją React (lub inną aplikacją JavaScript), gdzie `npm run build` tworzy statyczne pliki aplikacji.

2. **Zbuduj optymalizowany obraz:**
    - Ponownie zbuduj obraz z nowym Dockerfile, pamiętając o odpowiednim otagowaniu:
      ```
      docker build -t moja-aplikacja-webowa:optimized .
      ```

3. **Uruchom kontener z optymalizowanym obrazem:**
    - Uruchom kontener z nowym obrazem, tak jak w zadaniu 1.

4. **Weryfikacja:**
    - Sprawdź, czy aplikacja działa poprawnie po uruchomieniu z optymalizowanego obrazu, odwiedzając `http://localhost:8080`.
