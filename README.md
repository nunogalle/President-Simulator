import random

class Presidente:
    def __init__(self, nombre):
        self.nombre = nombre
        self.popularidad = 50  # Popularidad del presidente (0-100)
        self.deuda = 1000  # Deuda del país en millones
        self.economia = 50  # Indicador de economía (0-100)
        self.sanidad = 50  # Calidad del sistema de sanidad (0-100)
        self.educacion = 50  # Calidad del sistema educativo (0-100)
        self.defensa = 50  # Fuerza militar (0-100)
        self.relaciones_internacionales = 50  # Relaciones internacionales (0-100)

    def tomar_decision(self, decision):
        if decision == "aumentar_sanidad":
            self.sanidad += 5
            self.popularidad += 2
            print(f"{self.nombre} ha aumentado el presupuesto de sanidad. La popularidad sube.")
        elif decision == "reducir_deuda":
            self.deuda -= 100
            self.economia -= 2
            self.popularidad -= 3
            print(f"{self.nombre} ha reducido la deuda. Pero la economía se ve afectada a corto plazo.")
        elif decision == "mejorar_economia":
            self.economia += 10
            self.popularidad += 5
            print(f"{self.nombre} ha implementado políticas para mejorar la economía. La popularidad sube.")
        elif decision == "fortalecer_defensa":
            self.defensa += 5
            self.popularidad += 3
            print(f"{self.nombre} ha fortalecido las fuerzas armadas. La popularidad sube.")
        elif decision == "mejorar_relaciones_internacionales":
            self.relaciones_internacionales += 5
            self.popularidad += 4
            print(f"{self.nombre} ha mejorado las relaciones internacionales. La popularidad sube.")
        else:
            print("Decisión no válida.")

    def generar_evento(self):
        evento = random.choice([
            "crisis_economica", 
            "protestas_populares", 
            "alianza_internacional", 
            "catastrofe_natural",
            "descubrimiento_tecnologico"
        ])
        if evento == "crisis_economica":
            self.economia -= 15
            self.popularidad -= 10
            print(f"¡Una crisis económica ha golpeado el país! La economía se desploma.")
        elif evento == "protestas_populares":
            self.popularidad -= 10
            print(f"Se han desatado protestas populares en varias ciudades.")
        elif evento == "alianza_internacional":
            self.relaciones_internacionales += 10
            self.popularidad += 5
            print(f"Una nueva alianza internacional ha sido firmada, mejorando nuestra posición global.")
        elif evento == "catastrofe_natural":
            self.economia -= 10
            self.sanidad -= 5
            self.popularidad -= 5
            print(f"Una catástrofe natural ha afectado el país, la economía y la sanidad se ven afectadas.")
        elif evento == "descubrimiento_tecnologico":
            self.economia += 10
            self.popularidad += 7
            print(f"Un descubrimiento tecnológico ha revolucionado el país. La economía mejora.")

    def mostrar_estado(self):
        print(f"\nEstado actual del país bajo el liderazgo de {self.nombre}:")
        print(f"Popularidad: {self.popularidad}%")
        print(f"Deuda: {self.deuda} millones")
        print(f"Economía: {self.economia}/100")
        print(f"Sanidad: {self.sanidad}/100")
        print(f"Educación: {self.educacion}/100")
        print(f"Defensa: {self.defensa}/100")
        print(f"Relaciones internacionales: {self.relaciones_internacionales}/100")

# Función para interactuar con el presidente
def iniciar_simulador():
    nombre_presidente = input("Introduce el nombre del presidente: ")
    presidente = Presidente(nombre_presidente)
    
    while True:
        presidente.mostrar_estado()
        
        decision = input("\n¿Qué decisión quieres tomar? (aumentar_sanidad, reducir_deuda, mejorar_economia, fortalecer_defensa, mejorar_relaciones_internacionales): ")
        presidente.tomar_decision(decision)
        
        presidente.generar_evento()
        
        continuar = input("\n¿Quieres tomar otra decisión? (s/n): ")
        if continuar.lower() != "s":
            break

# Iniciar simulador
if __name__ == "__main__":
    iniciar_simulador()
