### DESAFÍO I

Células Procariotas:

No tienen núcleo definido.
Su ADN está en el citoplasma.
Carecen de organelas complejas.
Ejemplos: bacterias y arqueas.

Células Eucariotas:

Tienen un núcleo delimitado por una membrana.
Su ADN está en el núcleo.
Poseen organelas complejas (mitocondrias, cloroplastos).
Ejemplos: animales, plantas, hongos.


### DESAFÍO II

```python
# Diccionario con algunos codones de ARN de ejemplo
codigo_genetico = {
    'A': ['GCU', 'GCC', 'GCA', 'GCG'],
    'T': ['ACU', 'ACC', 'ACA', 'ACG'],
    'V': ['GUU', 'GUC', 'GUA', 'GUG'],
    'K': ['AAA', 'AAG'],
    'G': ['GGU', 'GGC', 'GGA', 'GGG'],
    'H': ['CAU', 'CAC'],
    'E': ['GAA', 'GAG'],
    'P': ['CCU', 'CCC', 'CCA', 'CCG'],
    'N': ['AAU', 'AAC'],
    'I': ['AUU', 'AUC', 'AUA'],
    'F': ['UUU', 'UUC'],
    'L': ['UUA', 'UUG', 'CUU', 'CUC', 'CUA', 'CUG'],
    'R': ['CGU', 'CGC', 'CGA', 'CGG', 'AGA', 'AGG'],
    'S': ['UCU', 'UCC', 'UCA', 'UCG', 'AGU', 'AGC'],
    'Q': ['CAA', 'CAG'],
    'C': ['UGU', 'UGC'],
    'Y': ['UAU', 'UAC'],
    'M': ['AUG'], # codón de inicio
}

# Secuencia proteica 
proteina = "ATVEKGGKHKTGPNEKGKKIFVQKCSQCHTVLHGLFGRKTGQA"

# funcion que da una secuencia de ARN
def obtener_arn(proteina):
    arn_secuencia = ""
    for aa in proteina:
        if aa in codigo_genetico:
            arn_secuencia += codigo_genetico[aa][0]  # Escoge el primer codón de cada aa
        else:
            arn_secuencia += '---'  # Indica error si el aa no está en el diccionario
    return arn_secuencia

print("ARN codificante:", obtener_arn(proteina))
```
### DESAFÍO III
```python
def buscar_caja_tata(secuencia):
    caja_tata = "TATAAA"
    posiciones = []
    for i in range(len(secuencia) - len(caja_tata) + 1):
        if secuencia[i:i+len(caja_tata)] == caja_tata:
            posiciones.append(i)
    return posiciones

# Lee el archivo
with open("secuencia_dna.txt", "r") as f:
    secuencia_dna = f.read().strip()

print("Posiciones de la caja TATA:", buscar_caja_tata(secuencia_dna))

```

### DESAFÍO IV
```python
import time
import random

def imprimir_con_retraso(texto, retraso=1):
    """Imprime el texto con un retraso entre líneas para crear efecto de narrativa."""
    for linea in texto.split('\n'):
        print(linea)
        time.sleep(retraso)

def inicio_juego():
    imprimir_con_retraso("""
    🧬 Bienvenido al Juego de la Expresión Génica RPG 🧬
    En este juego, eres una célula que debe completar la expresión génica.
    Tu misión es transformar la información en el ADN en una proteína funcional.
    
    Para ganar, tendrás que superar varias fases: transcribir el ADN, salir del núcleo,
    y traducir el ARN en una cadena de aminoácidos.
    
    ¡Buena suerte, héroe molecular! 🚀
    """, 1.5)

def fase1_transcripcion():
    imprimir_con_retraso("""
    === Fase 1: Transcripción ===
    Estás en el núcleo celular. Aquí, el ADN contiene todas las instrucciones necesarias.
    Para comenzar, debes transcribir una cadena de ADN en ARN mensajero (ARNm).
    
    Te proporciono una secuencia de ADN: 'ATGCATGC'
    Recuerda que la transcripción convierte:
    - A -> U
    - T -> A
    - G -> C
    - C -> G
    """, 1.5)
    
    secuencia_adn = "ATGCATGC"
    respuesta = input(f"¿Cuál sería la secuencia de ARN correspondiente a {secuencia_adn}? Escribe tu respuesta: ").upper()
    
    if respuesta == "UACGUACG":
        imprimir_con_retraso("""
        💥 ¡Correcto! Has transcrito el ADN en ARN mensajero.
        Ahora, el ARN está listo para salir del núcleo y ser traducido.
        """, 1)
    else:
        imprimir_con_retraso("""
        ❌ La secuencia de ARN no es correcta. Intenta de nuevo.
        """)
        fase1_transcripcion()  # Reintenta la fase

def fase2_salida_nucleo():
    imprimir_con_retraso("""
    === Fase 2: Salida del Núcleo ===
    Ahora que tienes el ARNm, necesitas llevarlo fuera del núcleo al citoplasma,
    donde se encuentran los ribosomas para la traducción.

    """, 1.2)

    # Desafío al jugador
    respuesta = input("Escribe 'salir' para llevar el ARN al citoplasma: ").strip().lower()
    if respuesta == "salir":
        imprimir_con_retraso("""
        🌊 ¡Bien hecho! El ARNm ha salido del núcleo y ha llegado al citoplasma.
        Ahora está listo para la traducción en los ribosomas.
        """, 1)
    else:
        imprimir_con_retraso("""
        ❌ No has salido del núcleo. La traducción no puede comenzar sin llevar el ARNm al citoplasma.
        ¡Inténtalo de nuevo!
        """)
        fase2_salida_nucleo()  # Reintenta la fase

def fase3_traduccion():
    imprimir_con_retraso("""
    === Fase 3: Traducción ===
    Ahora el ARNm se encuentra en el citoplasma, y los ribosomas están listos
    para decodificar la información en una secuencia de aminoácidos.

    Cada triplete de nucleótidos (codón) en el ARNm se convierte en un aminoácido.

    Te damos una secuencia de ARN: 'AUGUUUAG'
    Usa el código genético para traducirla en una cadena de aminoácidos.
    """, 1.5)

    secuencia_arn = "AUGUUUAG"
    respuesta = input(f"Traduce la secuencia {secuencia_arn} en una cadena de aminoácidos (usa los nombres de aminoácidos como Met, Phe, etc.): ").capitalize()
    
    if respuesta == "Met-Phe-Stop":
        imprimir_con_retraso("""
        🎉 ¡Correcto! Has traducido la secuencia de ARN en la proteína correcta.
        La secuencia es Met-Phe-Stop, lo que indica el comienzo y final de la proteína.
        """, 1)
    else:
        imprimir_con_retraso("""
        ❌ La traducción no es correcta. Intenta de nuevo.
        """)
        fase3_traduccion()  # Reintenta la fase

def fase4_empalme_arn():
    imprimir_con_retraso("""
    === Fase 4: Empalme de ARN (Splicing) ===
    El ARN transcrito contiene partes no codificantes llamadas **intrones**.
    Estas partes deben ser eliminadas para que el ARN funcional solo contenga **exones**.

    Aquí está tu ARN con intrones: 'AUGGUCUUAGGAAGCGAAUUUUGAGUGGAUCUAAGUAGGA'
    Elimina los intrones (UAA, UAG, UGA).
    """, 1.5)

    arn_con_intrones = "AUGGUCUUAGGAAGCGAAUUUUGAGUGGAUCUAAGUAGGA"
    print(f"Secuencia de ARN original con intrones: {arn_con_intrones}")

    # Eliminar los intrones (codones de terminación)
    arn_sin_intrones = arn_con_intrones.replace("UAA", "").replace("UAG", "").replace("UGA", "")
    print(f"Secuencia de ARN sin intrones: {arn_sin_intrones}")

    respuesta = input("Escribe la secuencia de ARN sin intrones: ").upper()
    if respuesta == arn_sin_intrones:
        imprimir_con_retraso("""
        💥 ¡Correcto! Has eliminado los intrones y ahora el ARN está listo para ser traducido.
        """, 1)
    else:
        imprimir_con_retraso("""
        ❌ La secuencia no es correcta. Los intrones no han sido eliminados adecuadamente. ¡Inténtalo de nuevo!
        """)
        fase4_empalme_arn()  # Reintenta la fase

def fase5_modificacion_adn():
    imprimir_con_retraso("""
    === Fase 5: Modificación de ADN ===
    El ADN tiene secuencias que codifican proteínas específicas. A veces, las células necesitan modificar
    estas secuencias para adaptarse a nuevas situaciones o cambiar la proteína que están produciendo.

    Aquí está tu secuencia de ADN original: 'ATGCGTAC'
    Cambia una base para que obtengas una secuencia que codifique para la proteína 'Met-Ser-Stop'.
    Recuerda, A -> U, T -> A, G -> C, C -> G.
    """, 1.5)

    secuencia_adn_original = "ATGCGTAC"
    respuesta = input(f"¿Cómo cambiarías la secuencia {secuencia_adn_original} para que se codifique la proteína 'Met-Ser-Stop'? ").upper()
    
    if respuesta == "ATGAGTAC":
        imprimir_con_retraso("""
        🎉 ¡Bien hecho! Has modificado correctamente la secuencia de ADN.
        El cambio ha permitido obtener la proteína 'Met-Ser-Stop'.
        """, 1)
    else:
        imprimir_con_retraso("""
        ❌ La modificación no es correcta. ¡Inténtalo de nuevo!
        """)
        fase5_modificacion_adn()  # Reintenta la fase

def jugar():
    inicio_juego()
    fase1_transcripcion()
    fase2_salida_nucleo()
    fase3_traduccion()
    fase4_empalme_arn()
    fase5_modificacion_adn()

# Inicia el juego
jugar()

```
