# Clínica Sonrisa Feliz - Sistema de Gestión Odontológica

Este es un sistema de escritorio robusto desarrollado en **Java** para la administración integral de una clínica dental. La aplicación está diseñada bajo una **arquitectura en capas** que separa estrictamente la interfaz de usuario, las reglas de negocio y el almacenamiento de datos, implementando las mejores prácticas del paradigma de Programación Orientada a Objetos (POO).

---

## 🏛️ Arquitectura del Sistema

El proyecto sigue una organización limpia y desacoplada estructurada en las siguientes capas lógicas:

1. **Capa de Presentación (`View`):** Interfaz gráfica de usuario (GUI) construida enteramente con **Java Swing** y **AWT**. Utiliza un contenedor principal (`MainFrame`) gestionado por un `CardLayout` para alternar fluidamente entre los distintos paneles del sistema. Los formularios extienden de una clase base común (`BaseFormPanel`) para estandarizar el diseño y la validación visual.
2. **Capa de Lógica de Negocio (`LogicaDeNegocio` / Services):** Clases controladoras (`ServicioPaciente`, `ServicioOdonto`, `ServicioTurno`) que procesan y validan las acciones del sistema antes de ser enviadas a la capa de persistencia.
3. **Capa de Persistencia (`Persistencia` / Repositories):** Repositorios encargados del ciclo de vida de los datos (`RepoPaciente`, `RepoOdonto`, `RepoTurno`), encargados de escribir y leer registros en archivos binarios locales.
4. **Capa de Entidades (`Entity`):** Clases del modelo de dominio que representan las estructuras de datos reales (`Paciente`, `Odontologo` con sus especialidades como `Ortodoncista` o `Periodoncista`, `Domicilio`, `Turno`, etc.).
5. **Capa de Gestión de Errores (`Excepciones`):** Excepciones personalizadas del dominio (`ClinicaException`) para capturar y controlar de forma segura cualquier fallo del negocio.

---

## 🚀 Características Principales

* **Módulo de Pacientes:** Registro completo de información personal, dirección física vinculada (`Domicilio`), DNI, correo electrónico y herramientas para la búsqueda rápida por apellido en tiempo real.
* **Módulo de Odontólogos:** Soporte de especialistas con cálculo o validación dinámica de acuerdo con su rama médica (`Ortodoncista`, `Periodoncista`, etc.).
* **Gestión de Turnos Avanzada:** Planificación de citas que vincula de manera dinámica a los pacientes con los profesionales de la salud, permitiendo filtrar turnos por DNI del paciente o matrícula del odontólogo.
* **Validación Visual Activa:** Los formularios controlan los campos obligatorios o formatos inválidos en tiempo de ejecución (ej. formato de DNI, correo electrónico con `@`), alertando visualmente al usuario al pintar los bordes de los campos erróneos en color rojo.
* **Persistencia Local Segura:** Almacenamiento local mediante serialización de objetos en archivos de datos binarios (`.dat`). Al cerrar la aplicación, se garantiza el resguardo completo de las colecciones (`HashMap`) del sistema.

---

## 📁 Estructura del Proyecto

El código fuente se organiza de la siguiente manera dentro del directorio raíz:

```text
├── ClinicaSonrisaFelizz.iml     # Configuración del módulo de IntelliJ IDEA
├── datos_odontologos.dat        # Archivo de persistencia binaria de los especialistas
├── datos_pacientes.dat          # Archivo de persistencia binaria de los pacientes
└── src/
    ├── Entity/                  # Clases de dominio (Paciente, Odontologo, Domicilio, etc.)
    ├── Excepciones/             # Gestión de errores personalizada (ClinicaException)
    ├── LogicaDeNegocio/         # Componentes de servicio y reglas del negocio
    ├── Persistencia/            # Repositorios y persistencia de archivos .dat
    └── View/                    # Formularios, componentes de UI y clase Main principal
