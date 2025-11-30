# Car Parking Checker

Aquest projecte s'ha desenvolupat com a treball final per l'assignatura **Visió per Computador** (UAB). L'objectiu principal és construir un programari que comprovi l'estat de les places d'aparcament en un aparcament: detectar si una plaça està buida o ocupada i, en cas d'ocupació, intentar identificar la matrícula, el color i, si és possible, la marca del vehicle.

🗂️ Fitxers principals:
- `CV_ANHYDRA.pdf`: Document final del projecte.
- `PresentacióFinalVC.pdf`: Presentació final del projecte.

📘 Notebooks i què fan:
- `frames_extractor.ipynb` — Extreu fotogrames d'un vídeo (1 fotograma per segon per defecte) i guarda les imatges a la carpeta `frames/`.
- `Generador_Plantilles_Binaries.ipynb` — Genera plantilles binàries (imatges) amb números i lletres per a la posterior identificació manual per template matching; desa-les dins de `plantilles/numeros/` i `plantilles/lletres/`.
- `CarParking.ipynb` — Implementació de la part **clàssica** amb OpenCV: detecció de línies (Hough + Canny), identificació d'espais d'aparcament, extracció dels recortes de vehicles (`coches/`) i primers intents per detectar la matrícula i la marca amb mètodes tradicionals i plantilles.
- `CarParkingAvançat.ipynb` — Implementació **moderna**: ús de models ONNX (per exemple YOLOv5) per a la detecció de vehicles i mètodes més robustos per a la detecció de línies (skimage, Hough probabilístic) i filtratge.
- `LicensePlateReader.ipynb` — Pipeline de lectura de matrícula: segmentació i extracció de la placa, binarització, extracció de caràcters, reconeixement amb plantilles i ús d'EasyOCR per obtenir una lectura automàtica.
- `proves.ipynb` — Notebook de proves i experiments: és el banc de proves on s'han experimentat diferents estratègies de preprocessat, bàsicament mètodes clàssics (Otsu, morfologia, segmentació) per comprovar i validar passos intermedis de l'algorisme.

📁 Carpetes rellevants:
- `frames/` — Fotogrames extrets del vídeo (entrada per als altres notebooks).
- `coches/` — Recortes de les imatges on apareixen vehicles (guardats des del processament).
- `plantilles/` — Plantilles binàries generades per caràcters (dins `lletres/` i `numeros/`).
- `logos/` — (Imatges d'insígnies o marques que es poden utilitzar per la detecció de la marca del vehicle).

⚙️ Requisits (bàsic):
- Python 3.8+  
- opencv-python
- numpy
- matplotlib
- scikit-image
- onnxruntime
- easyocr
- (Altres paquets que es puguin usar: torchvision/torch si s'utilitza la versió de model amb PyTorch, etc.)

Instal·lació ràpida (recomanat en un entorn virtual):

```powershell
pip install -r requirements.txt  # si no tens el requirements.txt, instal·lar manualment
pip install opencv-python numpy matplotlib scikit-image onnxruntime easyocr
```

💡 Ordre recomanat d'execució:
1. Si tens el vídeo d'entrada, obre i executa `frames_extractor.ipynb` per extreure els fotogrames a `frames/`.
2. Executa `Generador_Plantilles_Binaries.ipynb` per crear les plantilles si vols provar la detecció manual (template matching).
3. Prova `CarParking.ipynb` (mètodes clàssics) o `CarParkingAvançat.ipynb` (mètodes moderns) segons necessitis.
4. Executa `LicensePlateReader.ipynb` per provar la lectura de matrícules amb les plantilles i EasyOCR.
5. Usa `proves.ipynb` per fer experiments i ajustar paràmetres.

✅ Autors:
- Enric Ferrera González
- Miguel López Manzanares
- Joan Marc