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

![person2](https://github.com/user-attachments/assets/2c06e769-dc58-43f9-a88d-18054a697c2d)
![first_woman](https://github.com/user-attachments/assets/3de0a79c-0a2d-411d-9819-e785e5dbdf08)
