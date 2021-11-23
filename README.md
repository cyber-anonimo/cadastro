#include<iostream>
using namespace std;

struct cadastrar{
	string nome;
	int matricula;
};  

#include "cadastro.h"

int main(){
	
	cadastrar aluno;
	
	cout << "Nome do aluno: ";
	cin >> aluno.nome;
	cout << "Numero da matricula: ";
	cin >> aluno.matricula;
	
	
	std::ofstream arquivo;
    arquivo.open("alunos.ods", std::fstream::app);
	arquivo << aluno.nome << ";" << aluno.matricula << "\n";
    arquivo.close();
	
	return 0;
} 
