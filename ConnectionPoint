#include <iostream>
#include <list>
#include <vector>
using namespace std;


class Graph {
    int V; // No. of vertices

    // Pointer to an array containing adjacency lists
    list<int>* adj;

    
    void DFSUtil(int v, bool visited[], bool print);

public:
    Graph(int V); // Constructor
    ~Graph();
    void addEdge(int v, int w);
    int connectedComponents(int, bool);
    void createGraph();
    void print_connectedComponents();
    std::vector<int> find_connection_points();   
    void print_connectionPoints();
};


int Graph::connectedComponents(int vert = -1, bool print = false)
{
    int comp_count = 0;
    // Mark all the vertices as not visited
    bool* visited = new bool[V];
    for (int v = 0; v < V; v++) {
        visited[v] = false;
    }
    if (vert != -1) {
        visited[vert] = true;
    }
    for (int v = 0; v < V; v++) {
        if (visited[v] == false) {
            // print all reachable vertices
            // from v
            ++comp_count;
            DFSUtil(v, visited, print);
            if (print) {
                cout << "\n";
            }
        }
    }
    delete[] visited;
    return comp_count;
}

void Graph::DFSUtil(int v, bool visited[], bool print = false)
{
    visited[v] = true;
    if (print) {
        cout << v << " ";
    }
    list<int>::iterator i;
    for (i = adj[v].begin(); i != adj[v].end(); ++i)
        if (!visited[*i])
            DFSUtil(*i, visited, print);
}

Graph::Graph(int V)
{
    this->V = V;
    adj = new list<int>[V];
}

Graph::~Graph() { delete[] adj; }

// method to add an undirected edge
void Graph::addEdge(int v, int w)
{
    adj[v].push_back(w);
    adj[w].push_back(v);
}

std::vector<int> Graph::find_connection_points() {
    std::vector<int> con_points;
    int count = connectedComponents();
    for (int i = 0; i < V; ++i) {
        if (connectedComponents(i) > count) {
            con_points.push_back(i);
        }
    }
    return con_points;
}

void Graph::print_connectedComponents() {

    cout << "Following are connected components" << std::endl;
    connectedComponents(-1, true);
}

void Graph::print_connectionPoints() {
    std::cout << std::endl << " CONNECTION POINTS ARE  " << std::endl;
    std::vector<int> con_points = find_connection_points();
    for (auto& i : con_points) {
        std::cout << i << " ";
    }
    std::cout << std::endl;
}

void Graph::createGraph() {
    int x = 0;
    int y = 0;
    std::cout << std::endl << " Input Edges , input negative number when finish" << std::endl;
    while (true) {
        std::cin >> x >> y;
        if (x >= 0 && y >= 0) {
            addEdge(x, y);
        }
        else {
            break;
        }
    }
}


int main()
{
    std::cout << "Input graph vertex count > 0" << std::endl;
    int count;
    std::cin >> count;
    if (count < 1) {
        std::cout << "invalid vertex count ";
        std::terminate();
    }
    Graph g(count);
    g.createGraph();
    g.print_connectedComponents();
    g.print_connectionPoints();
    
    return 0;
}
