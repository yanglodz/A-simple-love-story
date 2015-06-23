# Movie Chooser 2
# Demonstrates radio buttons
from tkinter import *
class Application(Frame):
  """ GUI Application for favorite movie type. """
  def __init__(self, master):
    """ Initialize Frame. """
    super(Application, self).__init__(master)
    self.grid()
    self.create_widgets()
  def create_widgets(self):
    """ Create widgets for movie type choices. """
    # create description label
    Label(self, text = "Enter information for a new story").grid(row = 0, column = 0, sticky = W)
    Label(self, text = "Man Hero:").grid(row = 1, column = 0, sticky = W)
    Label(self,text  = "Woman Hero:").grid(row = 2, column = 0, sticky = W)
    Label(self,text  = "Verb:").grid(row = 3, column = 0, sticky = W)
    Label(self,text  = "Adjective(s):").grid(row = 4, column = 0, sticky = W)
    Label(self,text  = "stuff:").grid(row = 5, column = 0,sticky = W)
    # create text inpute
    self.ent1 = Entry(self)
    self.ent1.grid(row = 1, column = 1, sticky = W)
    self.ent2 = Entry(self)
    self.ent2.grid(row = 2, column = 1, sticky = W)
    self.ent3 = Entry(self)
    self.ent3.grid(row = 3, column = 1, sticky = W)
    # create variable for single, favorite type of movie
    self.Stuff = StringVar()
    self.Stuff.set(None)
    # create Checkbutton
    self.handsome = BooleanVar()
    self.rich = BooleanVar()
    self.smart = BooleanVar()
    Checkbutton(self, text = "handsomen",variable = self.handsome).grid(row = 4, column = 1, sticky = W)
    Checkbutton(self, text = "rich", variable = self.rich).grid(row = 4, column = 2, sticky = W)
    Checkbutton(self, text = "smart", variable = self.smart).grid(row = 4, column = 3, sticky = W)
    # create Comedy radio button 
    Radiobutton(self,text = "Flower",variable = self.Stuff,value = "sword.").grid(row = 5, column = 1, sticky = W)
    Radiobutton(self,text = "Diamond",variable = self.Stuff,value = "diamond.").grid(row = 5, column = 2, sticky = W)
    Radiobutton(self,text = "Poetry",variable = self.Stuff,value = "poetry.").grid(row = 5, column = 3, sticky = W)
    # create Button
    Button(self, text = "click for story",command = self.update_text).grid(row = 6, column = 0,sticky = W)
    # create text field to display result
    self.results_txt = Text(self, width = 80, height = 10,wrap = WORD)
    self.results_txt.grid(row = 7, column = 0, columnspan = 4)
  def update_text(self):
    """ Update text area and display user's favorite movie type. """
    adj = ""
    if self.handsome.get():
      adj += "handsome,"
    if self.rich.get():
      adj += "rich,"
    if self.smart.get():
      adj += "smart,"
    story = "  In the old days, There was a Hero, his name is "+ self.ent1.get() +". He is "+ adj +" honest and brave. He lived in a small village which is quiet and pacific. One day, "+ self.ent1.get() +" saw a girl named "+ self.ent2.get() +" who is a beautiful girl "+self.ent1.get()+" really love this girl......He bought a "+ self.Stuff.get() +" and would like to give it to the girl. Finally, "+self.ent1.get()+" found "+self.ent2.get()+". They feel very happy. "+self.ent1.get()+" give it to her and "+self.ent3.get()+" with "+self.ent2.get()+". In the end, "+self.ent1.get()+" has a lot of babies."
    #story += self.BodyPart.get()
    self.results_txt.delete(0.0, END)
    self.results_txt.insert(0.0, story)
# main
root = Tk()
root.title("Love ")
root.geometry("600x400")
app = Application(root)
root.mainloop()
