
#### PARA PENSAR
- **Genes "informacionales" vs. "operacionales"**: los genes que determinan características celulares y procesos vitales. Tienen diferentes orígenes evolutivos. Los "informacionales" son más relacionados con la herencia y regulación, mientras que los "operacionales" están más vinculados a funciones básicas de la célula.

#### DESAFÍO I: Diferencias entre células procariotas y eucariotas
**Núcleo**: Las eucariotas tienen un núcleo definido y las procariotas no.
**Organelas**: Eucariotas poseen organelas membranosas y procariotas carecen de ellas.
**Tamaño**: Generalmente, las eucariotas son más grandes.
**Reproducción**: Procariotas se reproducen principalmente por fisión binaria mientras que las eucariotas pueden tener mitosis y meiosis.

#### DESAFÍO II: Script en Python para secuencia de ARN codificante

```
def aminoacido_a_codones(aminoacido):
    codones = {
        
    }
    return codones.get(aminoacido, '')

def secuencia_a_arn(secuencia):
    arn = ''
    for aa in secuencia:
        arn += aminoacido_a_codones(aa)
    return arn

secuencia_proteica = 'ATVEKGGKHKTGPNEKGKKIFVQKCSQCHTVLHGLFGRKTGQA'
arn_codificante = secuencia_a_arn(secuencia_proteica)
print(arn_codificante)
```

#### DESAFÍO III: Script en Python para identificar regiones promotoras

```
def encontrar_promotores(archivo):
    with open(archivo, 'r') as file:
        secuencia = file.read()
        
    promotores = []
    inicio = secuencia.find('TATAAA')
    
    while inicio != -1:
        fin = secuencia.find('TATAAA', inicio + 6)
        if fin == -1:
            break
        promotores.append(secuencia[inicio:fin + 6])
        inicio = fin
    
    return promotores

archivo_dna = 'arxhivo.txt'
print(encontrar_promotores(archivo_dna))
```

#### DESAFÍO IV: Juego RPG interactivo
```
def juego_expresion_genica():
    print("¡Bienvenido al juego de la vida")
    print("Eres una célula eucariota que busca generar una proteína")
    
    while True:
        decision = input("¿Quieres Transcribir ADN o Traducir ARN? (ADN o ARN): ")
        if decision == 'ADN':
            print("¡Transcribiendo ADN a ARN mensajero!")
        elif decision == 'ARN':
            print("¡Traduciendo ARN a proteína!")
        else:
            print("Opción no válida. Intenta nuevamente.")
        
        continuar = input("¿Quieres continuar jugando? (si/no): ")
        if continuar.lower() != 'si':
            break

juego_expresion_genica()
```