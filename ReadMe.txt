Binary Search program 
Here is the Binary Search code for you to see


#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

#define longitud 5

void division(int arreglo1[],int valorACambiar, int posicion)
{
    for(int x = 0; x <= longitud-1; x++)
    {
        if (arreglo1[x] == valorACambiar)
            arreglo1[x] = posicion;
        cout<<arreglo1[x]<<" ";
    }

}
int binarySearch2(int array[], int cantidad, int valor)
{
    int start, end, mid;
    start = 0;
    end = cantidad-1;
    int count = 0;

    while(start <= end)
    {
        mid = (start + end)/2;
        if(array[mid] == valor)
        {
            count++;
            return count;
        }
        else if (valor > array[mid]) {
            start = mid + 1;
            count++;
        }
        else if (valor < array[mid])
        {end = mid - 1;
        count++;
        }
    }
    return 0;
}
int binarySearch(int array[], int cantidad, int valor)
{
    int start, end, mid;
    start = 0;
    end = cantidad-1;

    while(start <= end)
    {
        mid = (start + end)/2;
        if(array[mid] == valor)
            return mid;
        else if (valor > array[mid])
            start = mid+1;
        else if (valor < array[mid])
            end = mid - 1;
    }
    return 0;
}

void selectionSort(int list[])
{
    int index;
    int smallestIndex;
    int location;
    int temp;

    for(index = 0; index < longitud-1; index++)
    {
        smallestIndex = index;

        for(location =index +1; location <longitud;location++)
            if(list[location] < list[smallestIndex])
                smallestIndex = location;

        temp = list[smallestIndex];
        list[smallestIndex] = list[index];
        list[index] = temp;

    }
}

int main() {
    int  valor, cantidadDiv = 0;
    int arreglo[longitud];
    int arreglo2[longitud];



    for (int x = 0; x < longitud; x++)
    {
        arreglo[x] = 1 + rand() % 200;
    }

    for (int i = 0; i < longitud; i++)
    {
        cout<<arreglo[i]<< " " ;
    }

    selectionSort(arreglo);

    cout<<"\n--------------------------------"<< endl;

    for (int i = 0; i < longitud; i++)
    {
        cout<<arreglo[i]<< " " ;
    }
    cout<<"\n--------------------------------"<< endl;

    cout<<"Que numero desea buscar?";
    cin>>valor;

    cout<<"El numero esta en el indice: "<<binarySearch(arreglo, longitud, valor);

    cantidadDiv = binarySearch(arreglo, longitud, valor);

    cout<<"\nCantidad de veces que se divide el array: "<<cantidadDiv<<endl;
    cout<<"\n--------------------------------"<< endl;

    for (int i = 0; i < longitud; i++)
    {
        arreglo2[i]=arreglo[i];
    }
    for (int i = 0; i < longitud; i++)
    {
        cout<<arreglo[i]<<" ";
    }

        cout<<endl;

    division(arreglo2,valor,cantidadDiv);

    return 0;
}
