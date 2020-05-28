# Funciones-importantes

## Funcion para salto de linea
```
 verNombreSaltoLinea(nombreCompleto: string, hijos: number, maxLetrasPorFila = 13) {
        if (!nombreCompleto) return;
        nombreCompleto = nombreCompleto.trim()
        nombreCompleto = nombreCompleto.charAt(0).toUpperCase() + nombreCompleto.slice(1).toLowerCase();;
        let arrayNombres = nombreCompleto.split(' ');

        let letras = 0;
        let nuevoArray = [];
        let texto = '';

        arrayNombres.forEach((nombre, i) => {
            letras += nombre.length;
            if (letras >= maxLetrasPorFila) {
                if (texto.length == 0) {
                    texto = nombre;
                } else {
                    texto += ' ' + nombre;
                }
                nuevoArray.push(texto);
                letras = 0;
                texto = ''
            } else {
                texto += ' ' + nombre;
                if (arrayNombres.length == i + 1) {
                    nuevoArray.push(texto);
                }
            }
        })
        arrayNombres = nuevoArray;

        if (arrayNombres.length > 4) {
            arrayNombres = arrayNombres.slice(0, 4);
            arrayNombres[3] += `... (${hijos})`;
            return arrayNombres;
        }

        arrayNombres[arrayNombres.length - 1] += ` (${hijos})`;
        return arrayNombres
    }
    ```
