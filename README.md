#include "mainwindow.h"
#include <dialog2.h>
#include <QApplication>
#include <QApplication>
#include <QWidget>
#include <QLabel>
#include <QHBoxLayout>
#include <QLineEdit>
#include <QFormLayout>
#include <QPushButton>
#include <QSpacerItem>
#include <QTextEdit>
#include <QFormLayout>
#include <QLCDNumber>
#include <QGridLayout>

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
  QWidget* window=new QWidget();
   window->setWindowTitle("QHBox Layout test");
   window->windowTitle();
   window->resize(400,120);
    window->setStyleSheet("background-color : #1589FF");

    //
    QHBoxLayout *layout = new QHBoxLayout(window);

    //
    QLabel* label=new QLabel("<h2>Name:</h2>");
    label->setFont(QFont("times",12));
    layout->addWidget(label);
    //
     QLineEdit* name=new QLineEdit;
     layout->addWidget(name);
    //
     QPushButton* search=new QPushButton("Search");
     search->setFont(QFont("times",12));

     layout->addWidget(search);
     window->show();
   ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
   QWidget* wid=new QWidget();
   wid->setWindowTitle("Nested Layouts Test");
   QHBoxLayout* l1=new QHBoxLayout();
   QLabel* Name=new QLabel("<h2>Name:</h2>");
   l1->addWidget(Name);
   QLineEdit* e_box=new QLineEdit;
   l1->addWidget(e_box);

   QCheckBox* match=new QCheckBox("Match case");
   QCheckBox* search_backward=new QCheckBox("Search backward");

   QVBoxLayout* l3=new QVBoxLayout();
   l3->addLayout(l1);

   l3->addWidget(match);
   l3->addWidget(search_backward);
   QVBoxLayout* l4=new QVBoxLayout();
   QPushButton* search1=new QPushButton("Search");
   QPushButton* close=new QPushButton("Close");
   l4->addWidget(search1);
   l4->addWidget(close);
   l4->addStretch(1);
   QSpacerItem* t=new QSpacerItem(3,2);
   l4->addSpacerItem(t);
   QHBoxLayout* center=new QHBoxLayout();
   center->addLayout(l3);
   center->addLayout(l4);

   wid->setLayout(center);
   wid->show();
   //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
   QWidget* window3=new QWidget();
   window3->setWindowTitle("Report Bug");
   QList <QLabel*> my_label={new QLabel("Name"),new QLabel("Company"),new QLabel("Phone"),new QLabel("Email"),new QLabel("Problem title")};

   QList <QLineEdit*> my_list={new QLineEdit("Name"),new QLineEdit("Company"),new QLineEdit("Phone"),new QLineEdit("Email"),new QLineEdit("Problem title")};
   //QVBoxLayout* layout1=new QVBoxLayout();
   QFormLayout* f=new QFormLayout();
   for(int i=0;i<4;i++){


      f->addRow(my_label[i],my_list[i]);
   }
  QLabel* label1=new QLabel("Summary Information");
  QTextEdit* summary=new QTextEdit();
  f->addRow(label1,summary);
  QLabel* reproducibility=new QLabel("Reproducibility");
  QLineEdit* rep=new QLineEdit();
  f->addRow(reproducibility,rep);

  QList <QPushButton*> buttonlist={new QPushButton("Reset"),new QPushButton("Submit Bug Report"),new QPushButton("Dont Submit")};
  QHBoxLayout* button_layout=new QHBoxLayout();
  for(int i=0;i<3;i++){
      button_layout->addWidget(buttonlist[i]);
  }
  button_layout->insertSpacing(1,100);
  QVBoxLayout* main_layout=new QVBoxLayout(window3);
  main_layout->addLayout(f);
  main_layout->addLayout(button_layout);
   window3->show();
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
  QWidget* window4=new QWidget();
  window4->setWindowTitle("Numeric keypad");
  QLCDNumber* lcd=new QLCDNumber();
  lcd->setMinimumHeight(80);
  QGridLayout* grid=new QGridLayout(window4);
  grid->addWidget(lcd,0,0,2,3);
  QList <QPushButton*> buttonList;
  for(int i=0;i<10;i++){
      buttonList.insert(i,new QPushButton(QString::number(9-i)));
  }

  for(int i=0;i<10;i++){
      grid->addWidget(buttonList[i]);
  }
  QPushButton* enter=new QPushButton("Enter");
  grid->addWidget(enter,5,1,1,2);

  window4->show();
    return a.exec();

}
