public class Autor {
    private int cantidadPublicaciones;
    private String filiacion;
    private String lineaInvestigacion;
    private String nacionalidad;
    private String nombre;
    private Publicacion[] publicaciones;

    public Autor(int tamañoArreglo) {
        this.publicaciones = new Publicacion[tamañoArreglo];
        this.cantidadPublicaciones = 0;
    }

    public Autor(String filiacion, String lineaInvestigacion, String nacionalidad, String nombre, int tamañoArreglo) {
        this.filiacion = filiacion;
        this.lineaInvestigacion = lineaInvestigacion;
        this.nacionalidad = nacionalidad;
        this.nombre = nombre;
        this.publicaciones = new Publicacion[tamañoArreglo];
        this.cantidadPublicaciones = 0;
    }

    public void AgregarPublicacion(Publicacion publicacionNueva) {
        if (cantidadPublicaciones < publicaciones.length) {
            publicaciones[cantidadPublicaciones] = publicacionNueva;
            cantidadPublicaciones++;
        } else {
            System.out.println("No se pueden agregar más publicaciones.");
        }
    }

    public int getCantidadPublicaciones() {
        return cantidadPublicaciones;
    }

    public String getFiliacion() {
        return filiacion;
    }

    public String getLineaInvestigacion() {
        return lineaInvestigacion;
    }

    public String getNacionalidad() {
        return nacionalidad;
    }

    public String getNombre() {
        return nombre;
    }

    public Publicacion[] getPublicaciones() {
        return publicaciones;
    }

    public void setCantidadPublicaciones(int cantidadPublicaciones) {
        this.cantidadPublicaciones = cantidadPublicaciones;
    }

    public void setFiliacion(String filiacion) {
        this.filiacion = filiacion;
    }

    public void setLineaInvestigacion(String lineaInvestigacion) {
        this.lineaInvestigacion = lineaInvestigacion;
    }

    public void setNacionalidad(String nacionalidad) {
        this.nacionalidad = nacionalidad;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public void setPublicaciones(Publicacion[] publicaciones) {
        this.publicaciones = publicaciones;
    }

    @Override
    public String toString() {
        StringBuilder sb = new StringBuilder();
        sb.append("Autor{");
        sb.append("nombre='").append(nombre).append('\'');
        sb.append(", filiacion='").append(filiacion).append('\'');
        sb.append(", lineaInvestigacion='").append(lineaInvestigacion).append('\'');
        sb.append(", nacionalidad='").append(nacionalidad).append('\'');
        sb.append(", cantidadPublicaciones=").append(cantidadPublicaciones);
        sb.append(", publicaciones=[");
        for (int i = 0; i < cantidadPublicaciones; i++) {
            sb.append(publicaciones[i].toString());
            if (i < cantidadPublicaciones - 1) sb.append(", ");
        }
        sb.append("]}");
        return sb.toString();
    }
}



/modelopublicacion

public class Publicacion {
    private int año;
    private String nombreRevista;
    private String titulo;
    
    public Publicacion(int año,String nombreRevista, String titulo){
        this.año=año;
        this.nombreRevista=nombreRevista;
        this.titulo=titulo;
    }
    
    @Override
    public String toString(){
        return this.año+"-"+this.nombreRevista+"-"+this.titulo;
    }
}



//vistadeautor(falta importar)

public class vistaAutor {
    public static void main(String[] args) {
        controladorAutor controlador = new controladorAutor();

        Autor autor1 = controlador.crearAutor("Universidad XYZ", "Inteligencia Artificial", "Mexicana", "Juan Perez", 3);
        Publicacion pub1 = controlador.crearPublicacion(2020, "Revista Científica", "Investigación en AI");
        Publicacion pub2 = controlador.crearPublicacion(2021, "Revista de Tecnología", "Avances en Machine Learning");
        Publicacion pub3 = controlador.crearPublicacion(2022, "Revista de Innovación", "Nuevas técnicas en Deep Learning");

        controlador.AgregarPublicacion(pub1, autor1);
        controlador.AgregarPublicacion(pub2, autor1);
        controlador.AgregarPublicacion(pub3, autor1);

        System.out.println(controlador.imprimirAutor(autor1));

        Autor autor2 = controlador.crearAutor("Instituto ABC", "Robótica", "Peruana", "Maria Gonzalez", 3);
        Publicacion pub4 = controlador.crearPublicacion(2019, "Revista de Robótica", "Robots en la Industria");
        Publicacion pub5 = controlador.crearPublicacion(2020, "Revista de Innovación", "Avances en Robótica Médica");
        Publicacion pub6 = controlador.crearPublicacion(2021, "Revista Tecnológica", "Robots Autónomos");

        controlador.AgregarPublicacion(pub4, autor2);
        controlador.AgregarPublicacion(pub5, autor2);
        controlador.AgregarPublicacion(pub6, autor2);

        System.out.println(controlador.imprimirAutor(autor2));
    }
}

//Controlador
public class controladorAutor {
    public void AgregarPublicacion(Publicacion publicacionNueva, Autor autor) {
        try {
            autor.AgregarPublicacion(publicacionNueva);
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
    }

    public Autor crearAutor(String filiacion, String lineaInvestigacion, String nacionalidad, String nombre, int tamañoArreglo) {
        return new Autor(filiacion, lineaInvestigacion, nacionalidad, nombre, tamañoArreglo);
    }

    public Publicacion crearPublicacion(int año, String nombreRevista, String titulo) {
        return new Publicacion(año, nombreRevista, titulo);
    }

    public String imprimirAutor(Autor autor) {
        return autor.toString();
    }
}
