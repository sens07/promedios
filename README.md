# promedios

class GrupoCalificaciones:
    def __init__(self, estudiantes: int, materias: int):
        self.estudiantes = estudiantes
        self.materias = materias
        self.matriz = []

    def capturar(self):
        for i in range(self.estudiantes):
            fila = []
            print(f"\nEstudiante {i + 1}:")
            for j in range(self.materias):
                while True:
                    cal = float(input(f"  Calificación materia {j + 1} (0-100): "))
                    if 0 <= cal <= 100:
                        fila.append(cal)
                        break
                    print("  Debe estar entre 0 y 100.")
            self.matriz.append(fila)

    def mostrar_resultados(self):
        print("\n--- RESULTADOS ---")
        for i, fila in enumerate(self.matriz):
            print(f"Estudiante {i + 1} - Promedio: {sum(fila) / len(fila):.2f}")

        print()
        for j in range(self.materias):
            prom_mat = sum(self.matriz[i][j] for i in range(self.estudiantes)) / self.estudiantes
            print(f"Materia {j + 1} - Promedio: {prom_mat:.2f}")

        todas = [cal for fila in self.matriz for cal in fila]
        print(f"\nCalificación más alta: {max(todas):.2f}")
        print(f"Calificación más baja: {min(todas):.2f}")


estudiantes = int(input("¿Cuántos estudiantes hay? "))
materias = int(input("¿Cuántas materias hay? "))

grupo = GrupoCalificaciones(estudiantes, materias)
grupo.capturar()
grupo.mostrar_resultados()
