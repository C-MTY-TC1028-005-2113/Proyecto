# Avance1 Clase Serie y Clase Episodio

<img alt="points bar" align="right" height="36" src="../../blob/status/.github/activity-icons/points-bar.svg" />


```c++
//
//  main.cpp
//  Avance1
//
//  Created by Ma. Guadalupe Roque Díaz de León on 11/11/22.
//

#include <iostream>
#include <stdlib.h>
#include <stdio.h>
#include "Serie.h"
#include "Episodio.h"
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
    Episodio episodio1{"Graduacion", 1, 100};
    Serie serie1_22{"AAA","ITESM", 1000,"Aprendizaje", 100, 8};
    
    // 2º Declaración de variables
    int  opcion, temporada, duracion, calificacion, cantEpisodios;
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
                serie1_22.setID(id);
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
//  Test 1 - Avance1 
Datos de entrada:
8
11
1
AA1
Tec 21
2000
Aprendizaje
200
20
8
3
Tec 21 Objetos
8
4
10000
8
0

Datos de salida:
AAA,ITESM,1000,Aprendizaje,100,8
Graduacion,1,100
AA1,Tec 21,2000,Aprendizaje,200,20
AA1,Tec 21 Objetos,2000,Aprendizaje,200,20
AA1,Tec 21 Objetos,10000,Aprendizaje,200,20

Test 2 - Avance1

Datos de entrada:
11
10
Mi Graduacion
2
100
11
15
16
17
12
Mi Graduacion 2026
10
Mi Graduacion 2027
10
100
11
14
1000
11
0


Datos de salida:
Graduacion,1,100
Mi Graduacion,2,100
Mi Graduacion
2
100
Mi Graduacion 2027,10,100
Mi Graduacion 2027,10,1000


```

2. Push your changes back to your assignment GitHub repo. Remember to try to make your commits atomic and your commit messages descriptive.

3. Wait a minute for the tests to run. Refresh the repo page to see if you have completed the exercise successfully.
You should score 100 marks if the test passes.
