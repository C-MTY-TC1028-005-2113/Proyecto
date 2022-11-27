# Proyecto - entrega final

<img alt="points bar" align="right" height="36" src="../../blob/status/.github/activity-icons/points-bar.svg" />


```c++
//
//  main.cpp
//  
//
//  Created by Ma. Guadalupe Roque Díaz de León on 27/11/22.

#include <iostream>
#include <stdlib.h>
#include <stdio.h>
#include "Serie.h"
#include "Episodio.h"
#include "Series.h"
using namespace std;

void leerSerie(std::string &_id, std::string &_titulo, int &_duracion, std::string &_genero, int &_calificacion, int &_cantEpisodios){
    //cout << "Ingresa el id:";
    cin >> _id;
    
    //cout << "Ingresa el titulo:";
    cin.ignore();
    getline(cin, _titulo);
    
    //cout << "Ingresa la duracion en minutos:";
    cin >> _duracion;
    
   // cout << "Ingresa el genero:";
    cin >> _genero;
    
   // cout << "Ingresa la calificación:";
    cin >> _calificacion;
    
    //cout << "Ingresa la cantidad de episodios:";
    cin >> _cantEpisodios;
}

void leerEpisodio(std::string &_titulo, int &_temporada, int &_calificacion){
    //cout << "Ingresa titulo del Episodio:";
    cin.ignore();
    getline(cin, _titulo);
   //cout << "Ingresa temporada:";
    cin >> _temporada;
   // cout << "Ingresa calificación:";
    cin >> _calificacion;
}

int menu( ){ //: Función que despliega el siguiente menú de opciones y lee y retorna el valor leído
    int opcion;
    
    cin >> opcion;
    return opcion;
}

int main() {
    // 1º Declaración de objetos de las clase creadas, llamar a los constructores con parámatros
    // Titulo temporada calificacion
    Episodio episodio1{"GRADUACION", 1, 100}; // calificacion, episodios
    Serie serie1_22{"TEC","ITESM", 1000,"APRENDIZAJE", 0, 0};
    Series negocio;
    
    // 2º Declaración de variables
    int  index, opcion, temporada, duracion, calificacion, cantEpisodios;
    std::string id,titulo,genero;
   
    //* 3º Inicializar la vccc antes del ciclo
    opcion = menu();
    
    //* 4º Incluir la vccc dentro de la condicion del ciclo
    while (opcion != 0){
        
        //* 5º Determinar que hacer en cada opcion
        switch (opcion) {
            case 1:
                leerSerie(id, titulo, duracion, genero, calificacion, cantEpisodios);
                serie1_22 = Serie(id, titulo, duracion, genero, calificacion, cantEpisodios);
                break;
            case 2:
                //  cout << "Ingresa el nuevo id:";
                cin >> id;
                serie1_22.setId(id);
                break;
            case 3:
                //  cout << "Ingresa titulo:";
                cin.ignore();
                getline(cin, titulo);
                serie1_22.setTitulo(titulo);
                break;
            case 4:
                //  cout << "Ingresa duracion en minutos:";
                cin >> duracion;
                serie1_22.setDuracion(duracion);
                break;
            case 5:
                //   cout << "Ingresa genero:";
                cin >> genero;
                serie1_22.setGenero(genero);
                break;
            case 6:
                //  cout << "Ingresa calificación:";
                cin >> calificacion;
                serie1_22.setCalificacion(calificacion);
                break;
            case 7:
                //   cout << "Ingresa cantidad de episodios:";
                cin >> cantEpisodios;
                serie1_22.setCantidadEpisodios(cantEpisodios);
                break;
            case 8:
                // Desplegar la información de la serie
                cout << serie1_22.str() << endl;
                break;
            case 10:
                leerEpisodio(titulo, temporada, calificacion);
                episodio1 = Episodio(titulo, temporada, calificacion);
                break;
            case 11: // Desplegar el objeto de la clase Episodio
                cout << episodio1.str() << endl;
                break;
            case 12: // setTitulo
                cin.ignore();
                getline(cin, titulo);
                episodio1.setTitulo(titulo);
                break;
            case 13: // setTemporada
                cin >> temporada;
                episodio1.setTemporada(temporada);
                break;
            case 14: // setCalificacion
                cin >> calificacion;
                episodio1.setCalificacion(calificacion);
                break;
            case 15: // getTitulo
                cout << episodio1.getTitulo() << endl;
                break;
            case 16: // getTemporada
                cout << episodio1.getTemporada() << endl;
                break;
            case 17: // getCalificacion
                cout << episodio1.getCalificacion() << endl;
                break;
            case 18: //
                serie1_22.addEpisodio(Episodio{"Pozole Verde", 2, 100});// instancia anonima de la clase Episodio
                serie1_22.addEpisodio(Episodio{"Mangu Dominicano", 3, 100});
                serie1_22.addEpisodio(Episodio{"Machacado", 4, 100});
                break;
            case 19: //
                serie1_22.delEpisodio();
                break;
            case 20: //
                // se pide el episodio 1
                cin >> index;
                episodio1 = serie1_22.getEpisodio(index);
                if (index == -1){
                    cout << "No existe el episodio\n";
                }
                else{
                    cout << episodio1.str() << endl;
                }
                break;
            case 21: //
                serie1_22.calculaCalificacionPromedio();
                break;
            case 22: //
                negocio.leerArchivo();
                break;
            case 23: //
                negocio.calcularCalPromedioSerie();
                negocio.reporteFrecuenciasYPromedioSeries();
                break;
            case 24: //
                cout << negocio.getCantidadSeries() << endl;
                negocio.addSerie(serie1_22);
                cout << negocio.getCantidadSeries() << endl;
                break;
            case 25: //
                negocio.reporteFrecuenciasYPromedioSeries();
                break;
            default:
                break;
        }
        //* 6º Actualizar la vccc dentro del ciclo
        opcion = menu();

    }
    return 0;
}


```
# CASOS DE PRUEBA
```c++
/* Casos de Prueba
//  Test 1 - 
Datos de entrada:
8
11
2
TEC21
8
3
ITESM21
8
4
1
8
5
SUPER_APRENDIZAJE
8
0


Datos de salida:
TEC,ITESM,1000,APRENDIZAJE,0,0
  
GRADUACION,1,100
TEC21,ITESM,1000,APRENDIZAJE,0,0
  
TEC21,ITESM21,1000,APRENDIZAJE,0,0
  
TEC21,ITESM21,1,APRENDIZAJE,0,0
  
TEC21,ITESM21,1,SUPER_APRENDIZAJE,0,0

Test 2 -

Datos de entrada:
11
12
MI GRADUACION
13
2026
14
1000
11
0


Datos de salida:
GRADUACION,1,100
MI GRADUACION,2026,1000


Test 3 - 

Datos de entrada:
8
18
19
20
8
20
1
8
21
8
0


Datos de salida:
TEC,ITESM,1000,APRENDIZAJE,0,0
  
No existe el episodio
Mangu Dominicano,3,100
TEC,ITESM,1000,APRENDIZAJE,0,2
E0Pozole Verde,2,100
E1Mangu Dominicano,3,100
  
TEC,ITESM,1000,APRENDIZAJE,100,2
E0Pozole Verde,2,100
E1Mangu Dominicano,3,100

Test 4 - 

Datos de entrada:
22
25
0


Datos de salida:
Reporte
1,Su,1450,Dr,100,3
E0W,1,90
E1T,3,90
E2S,2,90
  
2,Bo,1440,Dr,100,0
  
3,Sa,3113,Dr,100,0
  
4,BB,1560,Dr,100,0
  
5,MK,123,Do,80,0
  
6,T,248,Th,90,0
  
7,Ch,330,Dr,90,0
  
8,A,484,Dr,100,2
E0H,1,90
E1G,1,90
  
9,W,600,Dr,100,0
  
Frecuencias
Dr,7,77
Do,1,11
Th,1,11
Total=9
Promedio=95

Test 5 - 

Datos de entrada:
22
25
0


Datos de salida:
Reporte
1,Su,1450,Dr,90,3
E0W,1,90
E1T,3,90
E2S,2,90

2,Bo,1440,Dr,0,0
  
3,Sa,3113,Dr,0,0
  
4,BB,1560,Dr,0,0
  
5,MK,123,Do,0,0
  
6,T,248,Th,0,0
  
7,Ch,330,Dr,0,0
  
8,A,484,Dr,90,2
E0H,1,90
E1G,1,90
  
9,W,600,Dr,0,0
  
Frecuencias
Dr,7,77
Do,1,11
Th,1,11
Total=9
Promedio=20

```

2. Push your changes back to your assignment GitHub repo. Remember to try to make your commits atomic and your commit messages descriptive.

3. Wait a minute for the tests to run. Refresh the repo page to see if you have completed the exercise successfully.
You should score 100 marks if the test passes.
