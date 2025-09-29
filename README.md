# TarefaEstruturaDeDadosTreino2P1

package model.estrutura;

import java.lang.Exception;
import model.estrutura.No;

public class CircularDupla<T> {
	private No<T> ultimo_elemento = null;
	private No<T> primeiro_elemento = null;
	
	// append
	// getLast
	// remove
	// total
	
	public void append(T elemento) {
		
		No<T> novo = new No<>(elemento);
		
        if (impedimento) {
            System.out.println("Não é possível adicionar log");
            return;
        }

        if (this.primeiro_elemento == null) {
            this.primeiro_elemento = novo;
            novo.setProximo(novo);
            novo.setAnterior(novo);
            quantidade = 1;
        } else if (quantidade < MAX_ELEMENTS) {
            No<T> buffer_ultimo = this.ultimo_elemento.getAnterior();
			No<T> buffer_proximo = this.ultimo_elemento.getProximo();
            novo.setProximo(buffer_proximo);
            novo.setAnterior(buffer_ultimo);
            buffer_proximo.setProximo(novo);
			buffer_ultimo.setAnterior(novo);

            this.ultimo_elemento = novo;
            quantidade++;
			
        } else {
			
            No<T> maisAntigo = this.primeiro_elemento.getProximo(); 
            maisAntigo.setValor(elemento); 
            this.primeiro_elemento = maisAntigo; 
			
        }
    }
	
	@Override
	public String toString() {
		if (this.ultimo_elemento == null) {
			return "[]";
		}
		
		int MAX_ELEMENTS = 5;
		
		StringBuilder builder = new StringBuilder("{");
		No<T> buffer = this.ultimo_elemento;
		builder.append(buffer.getValor());
		while(MAX_ELEMENTS > 1){
			builder.append(", ");
			buffer = buffer.getAnterior();
			builder.append(buffer.getValor());
			MAX_ELEMENTS -= 1;
		}
		builder.append("}");
		return builder.toString();
	}
}

-------------------------------------------------------------------------

package controller;

import model.estrutura.CircularDupla;
import model.estrutura.No;

public class CircularDuplaController{
	public CircularDuplaController(){
		super();
	}
	
	public String teste() throws Exception{
		CircularDupla lista = new CircularDupla();
		
		lista.append("um");
		lista.append("dois");
		lista.append("tres");
		lista.append("quatro");
		lista.append("cinco");
		lista.append("seis");
		lista.append("sete");
		lista.append("oito");
		lista.append("nove");
		lista.append("dez");
		lista.append("onze");
		lista.append("doze");
		lista.append("treze");
		lista.append("quatorze");
		lista.append("quinze");
		lista.append("dezesseis");
		
		return lista.toString();
	}
}

-------------------------------------------------------------------------

package model.estrutura;

public class No<T> {
	
	private T valor;
	private No<T> proximo;
	private No<T> anterior;
	
	public No(T valor) {
		this.proximo = null;
		this.anterior = null;
		this.valor = valor;
	}
	
	public T getValor() {
		return valor;
	}
	public void setValor(T valor) {
		this.valor = valor;
	}
	
	public No<T> getProximo() {
		return proximo;
	}
	public void setProximo(No<T> proximo) {
		this.proximo = proximo;
	}
	
	public No<T> getAnterior() {
		return anterior;
	}
	public void setAnterior(No<T> anterior) {
		this.anterior = anterior;
	}
	
	@Override
	public String toString() {
		return valor.toString();
	}
}

-------------------------------------------------------------------------

package view;

import controller.CircularDuplaController;

public class CircularDupla{
	public static void main(String[] args) {
		try{
			CircularDuplaController obj = new CircularDuplaController();
			System.out.println(obj.teste());
		} catch(Exception e){
			e.printStackTrace();
		}
	}
}
