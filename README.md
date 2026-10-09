#include <stdio.h>

int ciclos = 0;
int tiempo = 0;

int esperaAvenida = 20;
int esperaSecundaria = 12;

int avanzaronAvenida = 0;
int avanzaronSecundaria = 0;

int tiempoAvenida = 30;
int tiempoSecundaria = 20;

int vehiculos;
int opcion;

void mostrarMenu()
{
    printf("\n===== SIMULADOR DE TRAFICO =====\n");
    printf("1. Activar avenida principal\n");
    printf("2. Activar calle secundaria\n");
    printf("3. Consultar estado del trafico\n");
    printf("4. Avanzar al siguiente ciclo\n");
    printf("5. Finalizar simulacion\n");
    printf("Elige una opcion: ");
}

void activarAvenida()
{
    tiempoAvenida = 30;

    if (esperaAvenida > 15)
    {
        tiempoAvenida = tiempoAvenida + 10;

        if (tiempoAvenida > 40)
        {
            tiempoAvenida = 40;
        }
    }

    vehiculos = tiempoAvenida * 2;

    if (vehiculos > esperaAvenida)
    {
        vehiculos = esperaAvenida;
    }

    esperaAvenida = esperaAvenida - vehiculos;
    avanzaronAvenida = avanzaronAvenida + vehiculos;
    tiempo = tiempo + tiempoAvenida;

    printf("Avanzaron %d vehiculos de la avenida principal.\n", vehiculos);
}

void activarSecundaria()
{
    tiempoSecundaria = 20;

    if (esperaSecundaria > 15)
    {
        tiempoSecundaria = tiempoSecundaria + 10;

        if (tiempoSecundaria > 40)
        {
            tiempoSecundaria = 40;
        }
    }

    vehiculos = tiempoSecundaria;

    if (vehiculos > esperaSecundaria)
    {
        vehiculos = esperaSecundaria;
    }

    esperaSecundaria = esperaSecundaria - vehiculos;
    avanzaronSecundaria = avanzaronSecundaria + vehiculos;
    tiempo = tiempo + tiempoSecundaria;

    printf("Avanzaron %d vehiculos de la calle secundaria.\n", vehiculos);
}

void consultarEstado()
{
    printf("\n===== ESTADO DEL TRAFICO =====\n");
    printf("Ciclos realizados: %d\n", ciclos);
    printf("Vehiculos esperando en avenida: %d\n", esperaAvenida);
    printf("Vehiculos esperando en secundaria: %d\n", esperaSecundaria);
    printf("Vehiculos que avanzaron en avenida: %d\n", avanzaronAvenida);
    printf("Vehiculos que avanzaron en secundaria: %d\n", avanzaronSecundaria);
    printf("Tiempo transcurrido: %d segundos\n", tiempo);
}

void mostrarReporte()
{
    printf("\n===== REPORTE FINAL =====\n");
    printf("Ciclos realizados: %d\n", ciclos);
    printf("Vehiculos que avanzaron en avenida: %d\n", avanzaronAvenida);
    printf("Vehiculos que avanzaron en secundaria: %d\n", avanzaronSecundaria);
    printf("Total de vehiculos que avanzaron: %d\n", avanzaronAvenida + avanzaronSecundaria);
    printf("Vehiculos esperando en avenida: %d\n", esperaAvenida);
    printf("Vehiculos esperando en secundaria: %d\n", esperaSecundaria);
    printf("Tiempo total simulado: %d segundos\n", tiempo);
}

int main()
{
    do
    {
        mostrarMenu();
        scanf("%d", &opcion);

        switch (opcion)
        {
            case 1:
                activarAvenida();
                break;

            case 2:
                activarSecundaria();
                break;

            case 3:
                consultarEstado();
                break;

            case 4:
                ciclos++;

                printf("Ciclo %d completado.\n", ciclos);

                if (ciclos >= 10)
                {
                    opcion = 5;
                }
                break;

            case 5:
                printf("Finalizando simulacion.\n");
                break;

            default:
                printf("Opcion no valida.\n");
                break;
        }

    } while (opcion != 5);

    mostrarReporte();

    return 0;
}
