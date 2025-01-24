Nombre Diego Adaos Álvarez

-Algoritmo dijkstra ruta mas corta en un grafo

comando de compilacion: g++ grafoDijkstra.cpp -o main

Profesor, espero que me disculpe por actualizar esto a destiempo. Tuve problemas con la lectura del archivo en el codespace por la version de g++ en la que trabajé.
No modifiqué nada más, solo este readme.

remplazando con esta funcion debería funcionar bien:

vector<vector<int>> leerArchivo(string nombre) {
    ifstream archivo(nombre);
    if (!archivo.is_open()) {
        cerr << "Error al abrir el archivo" << endl;
        return {};
    }
    string linea;
    getline(archivo, linea); 
    int n = stoi(linea);

    vector<vector<int>> listaAdyacencia(n, vector<int>(n));

    for (int i = 0; i < n; ++i) {
        getline(archivo, linea);
        stringstream ss(linea);
        string valor;
        int j = 0;
        while (getline(ss, valor, ',')) {
            listaAdyacencia[i][j] = stoi(valor);
            ++j;
        }
    }
    archivo.close();
    return listaAdyacencia;
}
