rom os import system 
system ("clear")

asignaturas = []
promedio_final = {}  
alumnos = []


def menu():
    print("--- DUOC ---")
    print("1. Añadir alumnos")
    print("2. Añadir asignatura")
    print("3. Ingresar las notas")
    print("4. Cartola")
    print("5. Salida")

def agregar_alumno():
    nuevo_alumnos = input("Ingrese el nombre del alumno: ")
    if nuevo_alumnos not in alumnos:
        alumnos.append(nuevo_alumnos)
        print(f"El alumno {nuevo_alumnos} se registrado correctamente")
    else:
        print("El alumno ya esta registrado")
    print("Lista de alumnos")
    for alumno in alumnos:
        print("* " + alumno)



def agregar_asignatura():
    nueva_asignaturas = input("Ingrese una nueva asignatura: ")
    if nueva_asignaturas not in asignaturas:
        asignaturas.append(nueva_asignaturas)
        print(f"La asignatura {nueva_asignaturas} se registro correctamente")
    else:
        print("La asignatura ya esta añadida")
    print("Asignaturas actuales")
    for materia in asignaturas:
        print("* " + materia)
    
def ingresar_notas():
    if not asignaturas:
        print("Primero debe añadir asignaturas")
        return

    alumno = input("Ingrese el nombre del alumno para ingresar la nota : ")
    if alumno not in alumnos:
        print(" El alumno no está registrado.")
        return

    notas_alumno = {}
    for materia in asignaturas:
        while True:
            try:
                nota = float(input(f"Ingrese la nota de la asignatura {materia}: "))
                if 1.0 <= nota <= 7.0:
                    notas_alumno[materia] = nota
                    break
                else:
                    print("La nota debe estar entre 1.0 y 7.0")
            except ValueError:
                print("Debe ingresar un número válido.")

    promedio_final[alumno] = notas_alumno 
    print(" Notas ingresadas correctamente.")

def mostrar_cartola():
        if not promedio_final:
            print("Aun no se ha ingresado notas")
            return
          
        alumno = input("Ingrese el nombre del alumno: ")
        if alumno not in promedio_final:
            print("El alumno no tiene notas registradas")
            return
          
        print("---Cartola de notas---")  
        suma = 0
        contador = 0  
        suma = 0
        contador = 0
        for materia, nota in promedio_final[alumno].items():
            print(f"{materia}: {nota:.1f}")
            suma += nota
            contador += 1

        promedio = suma / contador
        print(f"Promedio final: {promedio:.1f}")

        if promedio >= 4.0 and promedio <= 7.0:
            print("Alumno aprobado.")
        else:
            promedio < 4.0 or promedio == 1.0
            print("Alumno reprobado.")


while True:
    menu()   
    try:
        opc = int(input("Elegia una opcion: "))
        
        if  opc == 1 :
                agregar_alumno()
        elif opc == 2 :
                agregar_asignatura()
        elif opc == 3 :
                ingresar_notas()
        elif opc == 4 :
                mostrar_cartola()
        elif opc == 5 :
            print("Saliendo del programa.... ")
            break
        else:
            print("Opción no válida.")
    except ValueError:
        print("Debe ingresar un número válido.")
