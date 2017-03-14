import sys
from PyQt4 import QtGui

class Main(QtGui.QMainWindow):
    def __init__(self, parent = None):
        QtGui.QMainWindow.__init__(self,parent)
        self.filename = ""
        self.initUI()
        self.setupHelpMenu()
	

    def initToolbar(self):
        self.newAction = QtGui.QAction(QtGui.QIcon("icons/new1.png"),"New",self)
        self.newAction.setShortcut("Ctrl+N")
        self.newAction.triggered.connect(self.new)

        self.openAction = QtGui.QAction(QtGui.QIcon("icons/open1.png"),"Open file",self)
        self.openAction.setShortcut("Ctrl+O")
        self.openAction.triggered.connect(self.open)

        self.saveAction = QtGui.QAction(QtGui.QIcon("icons/save1.png"),"Save",self)     
        self.saveAction.setShortcut("Ctrl+S")
        self.saveAction.triggered.connect(self.save)

        self.cutAction = QtGui.QAction(QtGui.QIcon("icons/cut1.png"),"Cut",self)
        self.cutAction.setShortcut("Ctrl+X")
        self.cutAction.triggered.connect(self.text.cut)

        self.copyAction = QtGui.QAction(QtGui.QIcon("icons/copy1.png"),"Copy",self)       
        self.copyAction.setShortcut("Ctrl+C")
        self.copyAction.triggered.connect(self.text.copy)

        self.pasteAction = QtGui.QAction(QtGui.QIcon("icons/paste1.png"),"Paste",self)
        self.pasteAction.setShortcut("Ctrl+V")
        self.pasteAction.triggered.connect(self.text.paste)

        self.undoAction = QtGui.QAction(QtGui.QIcon("icons/undo1.png"),"Undo",self)
        self.undoAction.setShortcut("Ctrl+Z")
        self.undoAction.triggered.connect(self.text.undo)

        self.redoAction = QtGui.QAction(QtGui.QIcon("icons/redo1.png"),"Redo",self)
        self.redoAction.setShortcut("Ctrl+Y")
        self.redoAction.triggered.connect(self.text.redo)


        self.syntaxPresentationNewLineAction = QtGui.QAction("Presentation",self)
        self.syntaxPresentationNewLineAction.triggered.connect(self.appendNewLinePresentation)

        self.syntaxDocumentationNewLineAction = QtGui.QAction("Documents",self)
        self.syntaxDocumentationNewLineAction.triggered.connect(self.appendNewLineDocumentation)

        self.syntaxBeginNewLineAction = QtGui.QAction("\\begin",self)
        self.syntaxBeginNewLineAction.triggered.connect(self.appendaNewLine)

        self.syntaxsNewLineAction = QtGui.QAction("\documentclass{article}",self)
        self.syntaxsNewLineAction.triggered.connect(self.appendbNewLine)

        self.syntaxtNewLineAction = QtGui.QAction("\usepackage{graphicx}",self)
        self.syntaxtNewLineAction.triggered.connect(self.appendcNewLine)

        self.syntaxuNewLineAction = QtGui.QAction("\end{document}",self)
        self.syntaxuNewLineAction.triggered.connect(self.appenddNewLine)

        boldAction = QtGui.QAction(QtGui.QIcon("icons/bold.png"),"Bold",self)
        boldAction.triggered.connect(self.bold)

        italicAction = QtGui.QAction(QtGui.QIcon("icons/italic.png"),"Italic",self)
        italicAction.triggered.connect(self.italic)

        underlAction = QtGui.QAction(QtGui.QIcon("icons/underline.png"),"Underline",self)
        underlAction.triggered.connect(self.underline)

	
        self.toolbar = self.addToolBar("Options")
        self.toolbar.addAction(self.newAction)
        self.toolbar.addAction(self.openAction)
        self.toolbar.addAction(self.saveAction)

        self.toolbar.addSeparator()
        self.toolbar.addAction(boldAction)
        self.toolbar.addAction(italicAction)
        self.toolbar.addAction(underlAction)
        self.toolbar.addAction(self.cutAction)
        self.toolbar.addAction(self.copyAction)
        self.toolbar.addAction(self.pasteAction)
        self.toolbar.addAction(self.undoAction)
        self.toolbar.addAction(self.redoAction)

        self.addToolBarBreak()

    def initMenubar(self):
      menubar = self.menuBar()
      file = menubar.addMenu("File")
      edit = menubar.addMenu("Edit")
      

      file.addAction(self.newAction)
      file.addAction(self.openAction)
      file.addAction(self.saveAction)

      edit.addAction(self.undoAction)
      edit.addAction(self.redoAction)
      edit.addAction(self.cutAction)
      edit.addAction(self.copyAction)
      edit.addAction(self.pasteAction)

      syntaxGenerator = menubar.addMenu("Syntax Generator")
      syntaxGenerator.addAction(self.syntaxPresentationNewLineAction)
      syntaxGenerator.addAction(self.syntaxDocumentationNewLineAction)

      syntaxHelper = menubar.addMenu("Syntax Helper")
      syntaxHelper.addAction(self.syntaxBeginNewLineAction)	
      syntaxHelper.addAction(self.syntaxsNewLineAction)	
      syntaxHelper.addAction(self.syntaxtNewLineAction)	
      syntaxHelper.addAction(self.syntaxuNewLineAction)	
    def initUI(self):
        self.text = QtGui.QTextEdit(self)
        self.initToolbar()
        self.initMenubar()
        self.text.setTabStopWidth(33)
        self.setCentralWidget(self.text)
        self.statusbar = self.statusBar()
        self.setGeometry(100,100,1030,800)
        self.setWindowTitle("L-Writer")
        self.setWindowIcon(QtGui.QIcon('bt.jpg'))

    def new(self):
        spawn = Main(self)
        spawn.show()

    def open(self):
        self.filename = QtGui.QFileDialog.getOpenFileName(self, 'Open File')
        if self.filename:
            with open(self.filename,"rt") as file:
                self.text.setText(file.read())

    def save(self):
	filename = QtGui.QFileDialog.getSaveFileName(self, 'Save File')
	f = open(filename, 'w')
	filedata = self.text.toPlainText()
	f.write(filedata)
	f.close() 

    def appendNewLinePresentation(self):
        self.text.append("\documentclass[11pt]{beamer}")

	self.text.append("\usepackage{graphicx}")
	self.text.append("\usepackage[utf8]{inputenc}")
	self.text.append("\usepackage{amsmath}")
	self.text.append("\usepackage{amsfonts}")
	self.text.append("\usepackage{amssymb}")
	self.text.append("\usepackage{hyperref}")
	self.text.append("\n")

	self.text.append("\\author{author names}")
	self.text.append("\\title{presentation name}")
	self.text.append("\institute{institute name} ")
	self.text.append("\date{\tdate}") 
	self.text.append("\subject{subject name}")
	self.text.append("\n")

	self.text.append("\\begin{document}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\titlepage")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{ABSTRACT}}")
	self.text.append("The abstract text goes here.")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{PROOF OF CONCEPT}}")
	self.text.append("(\\begin{itemize}")
	self.text.append("\item")
	self.text.append("\end{itemize}")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{EXISTING SYSTEM}}")	
	self.text.append("\\begin{itemize}")
	self.text.append("\item")
	self.text.append("\end{itemize}")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{EXISTING SYSTEM}}")
	self.text.append("\\begin{center}")
	self.text.append("\includegraphics[scale=0.2]{filename.png/jpg}")
	self.text.append("\end{center}")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{PROPOSED SYSTEM:}}")
	self.text.append("screenshots\\")
	self.text.append("stage number")
	self.text.append("\includegraphics[scale=.2]{filename.png/jpg}")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{PHASES OF PROJECT}}")
	self.text.append("description")
	self.text.append("\\begin{enumerate}")
	self.text.append("\item")
	self.text.append("\end{enumerate}")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{WORK OF FLOW}}")
	self.text.append("\\begin{center}")
	self.text.append("\includegraphics[scale=.2]{filename.png/jpg}")
	self.text.append("\end{center}")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{DATA FLOW}}")
	self.text.append("\\begin{center}")
	self.text.append("\includegraphics[scale=.2]{filename.png/jpg}")
	self.text.append("\end{center}")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{CONCLUSION}}")
	self.text.append("\\begin{itemize}")
	self.text.append("\conclusion goes here")
	self.text.append("\end{itemize}")
	self.text.append("\end{frame}")
	self.text.append("\n")

	self.text.append("\\begin{frame}")
	self.text.append("\\frame{\\frametitle{REFERENCES}}")
	self.text.append("\url{url}")
	self.text.append("\end{frame}")
	self.text.append("\end{document}")
	self.text.append("\n")

    def appendNewLineDocumentation(self):
	self.text.append("\document")
   	
    def appendaNewLine(self):
	self.text.append("\\begin")
    		
    def appendbNewLine(self):
	self.text.append("\documentclass{article}")
    def appendcNewLine(self):
	self.text.append("\usepackage{graphicx}")
    def appenddNewLine(self):
	self.text.append("\end{document}")
    def about(self):
        QtGui.QMessageBox.about(self, "About simple LaTex Editor",
                "<p>Simple <b>LaTex Editor</b> is created " \
                "for helping those who are not familiar using " \
                "complex UIs.Provides additional features such as " \
                "syntax generator,syntax helper etc.</p>")    
    def setupHelpMenu(self):
        helpMenu = QtGui.QMenu("Help", self)
        self.menuBar().addMenu(helpMenu)
        helpMenu.addAction("About", self.about)
    def bold(self):

        if True:

            self.text.append("\\textbf{}")

        else:

            self.text.setFontWeight(QtGui.QFont.Bold)

    def italic(self):

        state = self.text.fontItalic()

        self.text.append("\\textit{}")

    def underline(self):

        state = self.text.fontUnderline()

        self.text.append("\underline{}")


       
def main():
    app = QtGui.QApplication(sys.argv)
    main = Main()
    main.show()
    sys.exit(app.exec_())

if __name__ == "__main__":
    main()
