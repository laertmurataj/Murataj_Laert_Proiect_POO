#include <iostream>
using namespace std;

class Student {
private:
    string nume;
    int* varsta;
    const int ID;
    float nrPrezenta;
    static int totalStudents;
    int an;
    friend void processStudent(Student& s);
public:
    Student(int const ID, string nume, int* varsta, float nrPrezenta, int an) : ID(ID), nume(nume), varsta(varsta), nrPrezenta(nrPrezenta), an(an) {
        totalStudents++;
        this->varsta = new int[an];
        for (int i = 0; i < an; i++) {
            this->varsta[i] = this->an + 18;
        }
    }
    // Copy Constructor
    Student(const Student& s) : ID(s.ID), nume(s.nume), nrPrezenta(s.nrPrezenta), an(s.an) {
        this->varsta = new int[s.an];
        for (int i = 0; i < s.an; i++) {
            this->varsta[i] = s.varsta[i];
        }
    }
    // Getters
    string getNume() {
        return nume;
    }

    int* getVarsta() {
        return varsta;
    }

    int getID() {
        return ID;
    }

    float getNrPrezenta() {
        return nrPrezenta;
    }

    static int getTotalStudents() {
        return totalStudents;
    }

    int getAn() {
        return an;
    }

    // Setters
    void setNume(string nume) {
        this->nume = nume;
    }

    void setVarsta(int* varsta) {
        this->varsta = varsta;
    }

    void setNrPrezenta(float nrPrezenta) {
        this->nrPrezenta = nrPrezenta;
    }

    void setAn(int an) {
        this->an = an;
    }
    ~Student() {
        delete[] varsta;
    }

    Student() : ID(1023) {
        this->nume = "Laert";
        this->nrPrezenta = 9;
        this->an = 2;
        this->varsta = new int[this->an];
        for (int i = 0; i < an; i++) {
            this->varsta[i] = this->an + 18;
        }
    }
    void afisare() {
        cout << "Nume: " << this->nume << "\nID: " << this->ID << "\nNr.Prezenta: " << this->nrPrezenta << "\nAnul: " << this->an << "\nVarste: ";
        for (int i = 0; i < an; i++) {
            cout << this->varsta[i] << " ";
        }
        cout << endl;
    }
  
    //bool operator
    bool operator==( Student& other)  {
        return this->getNume() == other.getNume();
    }
    Student& operator++() {
        this->nrPrezenta++; 
        return *this; 
    }
    Student& operator--() {
        this->nrPrezenta-=2;
        return *this;
    }

};
void processStudent(Student& s) {
    cout << "Procesare Student: " << s.getNume() << "\nAn: " << s.getAn() << endl;
}
int Student::totalStudents = 10;

class NoteSeminar {
private:
    string nume;
    const int ID;
    float* puncteDePrezenta;
    static int nrTotalSeminar;
    friend void processNoteSeminar(NoteSeminar& s);

public:
    NoteSeminar(string nume, const int ID, float* puncteDePrezenta) :nume(nume), ID(ID), puncteDePrezenta(puncteDePrezenta) {
        this->nrTotalSeminar = 14;
        this->puncteDePrezenta = new float[nrTotalSeminar];
        for (int i = 0; i < nrTotalSeminar; i++) {
            this->puncteDePrezenta[i] = 1;
        }
    }
    NoteSeminar() : ID(1068), nume("Laert"), puncteDePrezenta(nullptr) {

    }

    void afiseazaNoteSeminar() {
        cout << "Nume: " << nume << "\nID: " << ID << "\nPuncte de Prezenta: ";
        for (int i = 0; i < nrTotalSeminar; i++) {
            cout << puncteDePrezenta[i] << " ";
        }
     
    }

    ~NoteSeminar() {
        delete[] puncteDePrezenta;
    }
    // Copy Constructor
    NoteSeminar(const NoteSeminar& ns) : ID(ns.ID), nume(ns.nume) {
        this->puncteDePrezenta = new float[nrTotalSeminar];
        for (int i = 0; i < nrTotalSeminar; i++) {
            this->puncteDePrezenta[i] = ns.puncteDePrezenta[i];
        }
    }
    //getters
    string getNume() {
        return nume;
    }

    int getID() {
        return ID;
    }

    float* getPuncteDePrezenta() {
        return puncteDePrezenta;
    }

    static int getNrTotalSeminar() {
        return nrTotalSeminar;
    }

    // Setters
    void setNume(string nume) {
        this->nume = nume;
    }

    void setPuncteDePrezenta(float* puncteDePrezenta) {
        this->puncteDePrezenta = puncteDePrezenta;
    }
    bool operator<(NoteSeminar& other) {
        this->getPuncteDePrezenta() < other.getPuncteDePrezenta();
    }
    NoteSeminar& operator++() {
        this->puncteDePrezenta++;
        return *this;
    }
    NoteSeminar& operator--() {
        this->puncteDePrezenta-=2;
        return *this;
    }
};
void processNoteSeminar(NoteSeminar& s) {
    cout << "\nStudent: " << s.getNume() << endl;
}

    
int NoteSeminar::nrTotalSeminar = 14;
class NotaFinal {
private:
    string nume;
    const int ID;
    int notaExamen;
    double* notafinala;
   static int nrTotalExamen;
   friend void processNotaFinal(NotaFinal& s);
public:
    NotaFinal(string nume, const int ID, int notaExamen, double* notafinala) :nume(nume), ID(ID), notaExamen(notaExamen), notafinala(notafinala) {
       this->notafinala = new double;
       *this->notafinala = 0.7 * notaExamen;
    }

  
    void afiseazaNotaFinala() {
        cout << "\nNume: " << nume << "\nID: " << ID <<"\nNota Examen: "<< notaExamen<<"\nNota Finala : " << *notafinala << endl;
    }

    ~NotaFinal() {
        delete notafinala;
    }
    // Copy Constructor
    NotaFinal(const NotaFinal& nf) : ID(nf.ID), nume(nf.nume), notaExamen(nf.notaExamen) {
        this->notafinala = new double;
        *this->notafinala = *nf.notafinala;
    }
    // Getters
    string getNume() {
        return nume;
    }

    int getID() {
        return ID;
    }

    int getNotaExamen() {
        return notaExamen;
    }

    double* getNotaFinala() {
        return notafinala;
    }

    static int getNrTotalExamen() {
        return nrTotalExamen;
    }

    // Setters
    void setNume(string nume) {
        this->nume = nume;
    }

    void setNotaExamen(int notaExamen) {
        this->notaExamen = notaExamen;
    }

    void setNotaFinala(double* notafinala) {
        this->notafinala = notafinala;
    }
    bool operator<(NotaFinal& other) {
        this->getNotaExamen() < other.getNotaExamen();
    }
    NotaFinal operator++() {
        this->notafinala++;
        return *this;
    }
    NotaFinal operator--() {
        this->notafinala-=2;
        return *this;
    }
   
};

int NotaFinal::nrTotalExamen = 0;
    


int main() {
    Student s1;
    s1.afisare();
    Student s2(1202, "Andrei", new int[3]{1,2,3}, 9, 3);
    s2.afisare();
    NoteSeminar ns1("Laert", 1023, new float[14]);
    ns1.afiseazaNoteSeminar();
    NotaFinal nf1("Laert", 1027, 9, new double);
    nf1.afiseazaNotaFinala();
    Student s;
    s.setNume ("Laert");
    s.setAn (2);
    processStudent(s);
    NoteSeminar n;
    n.setNume("Andrei");
    processNoteSeminar(n);
     
    Student l;
    l.setNume("Laert");
    l.setNrPrezenta(9);
    cout << "Prezent: " << l.getNrPrezenta() << endl;
    ++l; 
    cout << "Dupa: " << l.getNrPrezenta() << endl;

        
   

   
    return 0;
}
