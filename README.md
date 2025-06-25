# Projeto-Final-Tkinter
#Ultimo projeto com tkinter que fizemos no primeiro trimestre do curso.

from tkinter import *
from tkinter import Tk, ttk
from tkinter import messagebox


co1 = "#2B1D08"
co2 = "#686144"
co3 = "#38576B"
co4 = "#85610D"
co5 = "#D8BA8F"


janela = Tk()
janela.title("")
janela.geometry("510x500")
janela.configure(bg=co1)
janela.resizable(False, False)


frame_cima = Frame(janela, width=510, height=50, bg= co1, relief="flat")
frame_cima.grid(row=0, column=0, pady=1, padx=0, sticky=NSEW)
frame_baixo = Frame(janela, width=510, height=300, bg= co1, relief="flat")
frame_baixo.grid(row=1, column=0, pady=1, padx=0, sticky=NSEW)


l_nome = Label(frame_cima, text="LOGIN", height=1, anchor=NE, font=('Ivy 25'), bg=co1, fg=co4)
l_nome.place(x=200, y=5)


l_linha = Label(frame_cima, width=275, text="", height=1, anchor=NW, font=('Ivy 25'), bg=co2)
l_linha.place(x=0, y=45)


credenciais = ['vitor', '9664']


def verificar_senha():
    nome = e_nome.get()
    senha = str(e_pass.get())


    if nome == 'admin' and senha == 'admin':
        messagebox.showinfo('Login', 'Seja bem vindo Admin!!!'+credenciais[0])
    elif credenciais[0] == nome and credenciais[1] == senha:
        messagebox.showinfo('Login', 'Seja bem vindo de volta'+credenciais[0])


        for widget in frame_baixo.winfo_children():
            widget.destroy()


        nova_janela()
    else:
        messagebox.showwarning('Erro', 'Verifique o nome de usuario ou a palavra passe')


def nova_janela():
    l_nome = Label(frame_cima, text="Usuario: " + credenciais[0], height=1, anchor=NE, font=('Ivy 20'), bg=co1, fg=co4)
    l_nome.place(x=5, y=5)


    l_linha = Label(frame_cima, width=275, text="", height=1, anchor=NW, font=('Ivy 1'), bg=co2)
    l_linha.place(x=10, y=45)


    l_nome = Label(frame_baixo, text="O que deseja verificar:", height=1, anchor=NE, font=('Ivy 20'), bg=co1, fg=co4)
    l_nome.place(x=120, y=80)


    botao_confirmar_hora = Button(frame_baixo, text="Ver hora da criacao.", width=39, height=2, bg=co2, fg=co1, font=('Ivy 8 bold'), relief=RAISED, overrelief=RIDGE, command=limpar_Tela)
    botao_confirmar_hora.place(x=120, y=220)
   
    botao_confirmar_data = Button(frame_baixo, text="Ver data da criacao.", width=39, height=2, bg=co2, fg=co1, font=('Ivy 8 bold'), relief=RAISED, overrelief=RIDGE, command=limpar_Tela2)
    botao_confirmar_data.place(x=120, y=260)


def limpar_Tela():
    for widget in frame_baixo.winfo_children():
            widget.destroy()


    ver_hora()


def limpar_Tela2():
    for widget in frame_baixo.winfo_children():
            widget.destroy()


    ver_data()


def ver_hora():


    l_nome = Label(frame_baixo, text="Hora: 10:48.", height=1, anchor=NW, font=('Ivy 10 bold'), bg=co1, fg=co4)
    l_nome.place(x=120, y=20)


def ver_data():


    l_nome = Label(frame_baixo, text="Data: 25/06/2025.", height=1, anchor=NW, font=('Ivy 10 bold'), bg=co1, fg=co4)
    l_nome.place(x=120, y=20)


l_nome = Label(frame_baixo, text="Nome *", height=1, anchor=NW, font=('Ivy 10 bold'), bg=co1, fg=co4)
l_nome.place(x=120, y=20)
e_nome = Entry(frame_baixo, width=25, justify='left', font=("", 15), highlightbackground=co1, relief="solid")
e_nome.place(x=120, y=50)


l_pass = Label(frame_baixo, text="password *", height=1, anchor=NW, font=('Ivy 10 bold'), bg=co1, fg=co4)
l_pass.place(x=120, y=95)
e_pass = Entry(frame_baixo, show='*',  width=25, justify='left', font=("", 15), highlightbackground=co1, relief="solid")
e_pass.place(x=120, y=130)


botao_confirmar = Button(frame_baixo, text="Entra", width=39, height=2, bg=co2, fg=co1, font=('Ivy 8 bold'), relief=RAISED, overrelief=RIDGE, command=verificar_senha)
botao_confirmar.place(x=120, y=180)


janela.mainloop()
