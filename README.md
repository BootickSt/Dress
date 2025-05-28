# Dress
Models: <br>   
RealVisXL<br>
control_v11p_sd15_depth<br>
ip-adapter-plus_sd15<br>
![Model](https://github.com/user-attachments/assets/309e7c69-4cd0-418b-91ad-18158abd94f2)

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

        Позитивный промпт (описание платья).

        Негативный промпт (ухудшающие слова).

4. Генерация изображения

    EmptyLatentImage – создает пустое латентное изображение (720x960).

    IPAdapterAdvanced – применяет стиль с IP-Adapter.

    ControlNetApplyAdvanced – контролирует композицию через ControlNet (Depth).

    KSampler – генерирует изображение (20 шагов, CFG=5, экспоненциальный шедулер).

5. Сохранение результата

    VAEDecode – декодирует латентное изображение в PNG.

    SaveImage – сохраняет результат.
