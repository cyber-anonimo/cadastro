#include "cadastro.h"

int CadastrarAlunos(){
	Alunos aluno;	
	
	for(int i = 0; i < 3; i++){
	cout << "Nome do aluno: ";
	cin >> aluno.nome;
	cout << "Numero da matricula: ";
	cin >> aluno.matricula;
	
	ofstream arquivo;
	arquivo.open("alunos.csv", fstream::app);
	arquivo << "Nome do aluno: " << aluno.nome << "\n"
			<< "Numero da matricula: " << aluno.matricula << "\n";
	arquivo.close();	
	}
}

int CadastrarNotas(){
	
		Notas aluno[3];
	
	for(int i = 0; i < 3; i++){
		cout << "\nNome do aluno: ";
		cin >> aluno[i].nome;
		cout << "Nota da aep do 1° semestre: ";
		cin >> aluno[i].aep1;
		cout << "Nota da prova do 1° semestre: ";
		cin >> aluno[i].prova1;
		cout << "Nota da aep do 2° semestre: ";
		cin >> aluno[i].aep2;
		cout << "Nota da prova do 2° semestre: ";
		cin >> aluno[i].prova2;

		aluno[i].media1 = aluno[i].aep1 + aluno[i].prova1;
		cout << "Media Final do 1° semestre: " << aluno[i].media1;
	
		aluno[i].media2 = aluno[i].aep2 + aluno[i].prova2;
		cout << "\nMedia Final do 2° semestre: " << aluno[i].media2;
		
		if(aluno[i].media1 < 6 && aluno[i].media2 < 6){
			cout << "\nNota da prova substitutiva";
			cin >> aluno[i].sub1;
			cin >> aluno[i].sub2;
			aluno[i].mediaFinal = aluno[i].sub1 + aluno[i].sub2;
			cout << aluno[i].mediaFinal;
		}else{
			cout << "\nO aluno " << aluno[i].nome << " não tem a obrigação de fazer a prova substutiva.";
		}

		if(aluno[i].media1 > 6.0 && aluno[i].media2 > 6.0){
			cout << "\nO aluno " << aluno[i].nome <<  " está aprovado.\n";
		}else{
			cout << "\nO aluno " << aluno[i].nome << " está reprovado.\n";
		}
	ofstream arquivo; //<< "\n"<< "Aep 1°bim" << ";" << "\n"  //<< "Prova 1°bim"
	arquivo.open("notas.csv", fstream::app);
	arquivo << "Nome do aluno" << ";" << "Aep do 1° bim" << "\n"
			<< aluno.nome << ";" << aluno.aep1 << ";"; //<< aluno[i].prova1;
	arquivo.close();
	}
}
void arquivo(Notas aluno){
	ofstream arquivo; //<< "\n"<< "Aep 1°bim" << ";" << "\n"  //<< "Prova 1°bim"
	arquivo.open("notas.csv", fstream::app);
	arquivo << "Nome do aluno" << ";" << "Aep do 1° bim" << ";" << "Prova do 2° bim" << ";" << "Sub do 1° bim" << ";" << "Sub do 2° bim" 
			<< aluno.nome << ";" << aluno.aep1 << ";" << aluno[i].prova1;
	arquivo.close();

}

int main(){
	Notas aluno;
	setlocale(LC_ALL, "portuguese");
	char escolha = ' ';
	cout << "Digite 'A' para cadastrar alunos novos.\n";
	cout << "Digite 'N' para cadastrar as notas dos alunos.\n";
	cin >> escolha;
	
		switch (escolha) {
		case 'A':
			CadastrarAlunos();
			arquivo(aluno);
		break;
		case 'N':
			CadastrarNotas();
			arquivo(aluno);
		break;
		}

return 0;
}






