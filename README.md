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
