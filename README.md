# Dress
Models: <br>   
RealVisXL<br>
control_v11p_sd15_depth<br>
ip-adapter-plus_sd15<br>
![Model](https://github.com/user-attachments/assets/4f5df3f8-15e4-4b32-a4b8-7b946095a4c6)


1. Загрузка моделей

    CheckpointLoaderSimple – загружает основную SD-модель (RealVisXL.safetensors).

    IPAdapterModelLoader – загружает IP-Adapter (ip-adapter-plus_sd15.bin).

    ControlNetLoader – загружает ControlNet (control_v11p_sd15_depth.pth).

    CLIPVisionLoader – загружает CLIP Vision (model.safetensors).

2. Обработка изображений

    LoadImage (x2) – загружает изображения (person.png и 4000274576284.jpg).

    PrepImageForClipVision – подготавливает изображение для CLIP Vision.

3. Текстовые промпты

    CLIPTextEncode (x2) – кодирует:
       Позитивный и негативный.

5. Генерация изображения

    EmptyLatentImage – создает пустое латентное изображение (720x960).

    IPAdapterAdvanced – применяет стиль с IP-Adapter.

    ControlNetApplyAdvanced – контролирует композицию через ControlNet (Depth).

    KSampler – генерирует изображение (20 шагов, CFG=5, экспоненциальный шедулер).

6. Сохранение результата

    VAEDecode – декодирует латентное изображение в PNG.

    SaveImage – сохраняет результат.
В данном задании использовал control_v11p_sd15_depth для того, что бы оставить нужную нам фигуру, а модель ip-adapter-plus_sd15 для того что бы перенести платье со второго изображения.
Модели Lora не использовал.
Много времени ушло на настройку гиперпараметров, что бы получались хотя бы какие то адекватные похожие изображения.
Пробовал применить маску на платье, но оказалось она и без нее отлично генерирует нужное платье.
Трудности возникли при генерации первой девушки, так как длинна платьев была разная, и следовательно новое, сгенерированное платье, было длиннее изначального.
Решил тем, что воспользовался img2img inpaint, непосредственно уже в webui интерфейсе, укоротил ей только платье, что бы оно соответсвовало исходному.
Вторая девушка получилась хорошо достаточно быстро, так как ее исходное платье не сильно отличалось по длинне.

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/2c06e769-dc58-43f9-a88d-18054a697c2d" alt="person2" width="300"></td>
    <td><img src="https://github.com/user-attachments/assets/eb747404-d786-4560-bb06-93d6763945c2" width="300"></td>
  </tr>
</table>

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/d4b2ecac-f214-485a-b57d-28cfa69dcbb0" alt="person2" width="300"></td>
    <td><img src="https://github.com/user-attachments/assets/5b32e428-0aac-48cc-9de8-699a41c92111" alt="first_woman" width="300"></td>
  </tr>

</table>

Платье было взято с данной картинки:
![4000274576284](https://github.com/user-attachments/assets/4768b8bf-fd41-40a5-a2de-a132e2981bb5)



Трудности встретелись в настройке гиперпараметров, что бы получить желанный результат.
С чем не удалось до конца справиться, так это с цветом женщины, преобладает цвет, взятый с картинки где платье.


