# Pokemo-Angola

import java.util.Scanner;
import java.util.Random;

public class PokemonAngola {
	
	static int AtaqueUsuario(){
		Scanner leitor = new Scanner(System.in);
		System.out.println("Escolha o ataque:");
		System.out.println("(1) Soco");
		System.out.println("(2) Especial");
		return leitor.nextInt();
	}
	
	static int AtaqueComputador() {
		Random gerador = new Random();
		return gerador.nextInt(3)+1; //Retorna número entre 1 e 3.
	}
	
	static void imprimeHP(int hpUsuario, int hpComputador, int contagemEspeciais) {
		
		System.out.println("==========================");
		System.out.println(" - Sua vida - "+ hpUsuario);
		System.out.println(" - Vida do adversario - "+ hpComputador);
		System.out.println(" * Contagem especiais * "+ contagemEspeciais);
		System.out.println("==========================");
	}
	
	static void batalha() {
		
		int hpUsuario = 150;
		int hpComputador = 15;
		int contagemEspeciais = 5;
		int escolhaAtaque;
		
		while(hpUsuario > 0 && hpComputador > 0) {
		imprimeHP(hpUsuario, hpComputador, contagemEspeciais);
		escolhaAtaque = AtaqueUsuario();
		switch(escolhaAtaque) {
		
		case 1:
			hpComputador -= 7;
			System.out.println("Jogador deu um soco.");
			break;
			
		case 2:
			hpComputador -= 20;
			contagemEspeciais --;
			System.out.println("Jogador deu um ATAQUE ESPECIAL!!");
			break;
		
		default:
			System.out.println("opção invalida.");
			break;
		
		}
		if(hpComputador > 0) {
			escolhaAtaque = AtaqueComputador();
			switch(escolhaAtaque) {
			
			case 1:
				hpUsuario -= 3;
				System.out.println("Computador aplicou um soco.");
				break;
			 
			case 2:
				hpUsuario -= 4;
				System.out.println("Computador deu um chute.");
				break;
			
			case 3:
				hpUsuario -= 6;
				System.out.println("Computador lançou o ATAQUE ESPECIAL!!");
				break;
			
			}
		}
		else{
			System.out.println("Inimigo derrotado.");
		}
		
		}
	}
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner leitor = new Scanner(System.in);
		int continua = 1;
		while(continua == 1) {			
			
			batalha();
			
			System.out.println("Fim de jogo. Deseja continuar jogando? (1)Sim (2)Não");
			continua = leitor.nextInt();
		}
	
	
	}

}
