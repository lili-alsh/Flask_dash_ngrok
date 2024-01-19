# Flask_dash_ngrok
Создание приложения Flask

## Задача - создать Flask app по заданным точкам x, y из входного файла подогнать полиномиальную функцию и вывести изображение в браузере

### Источники данных
В качестве входных параметров используем точки x, y из [файла для запроса Flask](https://github.com/lili-alsh/Flask_dash_ngrok/blob/main/%D1%84%D0%B0%D0%B9%D0%BB%20%D0%B4%D0%BB%D1%8F%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D0%B0%20Flask.csv)

###  Используемые методы
1. np.polyfit и np.poly1d
   Обучаем полином 4 степени и 30 степени на входных данных с помощью np.polyfit. Создаем полиномиальную функцию, которую в дальнейшем будем использовать для визуализации и вычислений с помощью np.poly1d.
   ```
            x = df['train_x']
            y = df['train_y']
            x = np.array(x)
            y = np.array(y)
            z = np.polyfit(x, y, 4)
            p = np.poly1d(z)
            p30 = np.poly1d(np.polyfit(x, y, 30))
   ```
2. Используем ngrok для создания туннеля.
   Имеются некоторые особенности установки
   ```
   !mkdir -p /drive/ngrok-ssh
   %cd /drive/ngrok-ssh
   !wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip -O ngrok-stable-linux-amd64.zip
   !unzip -u ngrok-stable-linux-amd64.zip
   !cp /drive/ngrok-ssh/ngrok /ngrok
   !chmod +x /ngrok
   ```
   Также в конце нужно не забыть авторизоваться
   ```
   !/ngrok authtoken
   ```
4. 
