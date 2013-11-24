unit Unit1;

{$mode objfpc}{$H+}

interface

uses
 Classes, SysUtils, FileUtil, TAGraph, TASeries, Forms, Controls, Graphics,
 Dialogs, StdCtrls;

type

 { TForm1 }

 TForm1 = class(TForm)
   Button1: TButton;
   Button2: TButton;
   Button3: TButton;
   Chart1: TChart;
   Chart1LineSeries1: TLineSeries;
   Label1: TLabel;
   Label2: TLabel;
   Memo1: TMemo;
   procedure Button1Click(Sender: TObject);
   procedure Button2Click(Sender: TObject);
   procedure Button3Click(Sender: TObject);
 private
   { private declarations }
 public
   { public declarations }
 end;

var
 Form1: TForm1;

const
 e = 0.001;

implementation

{$R *.lfm}

{ TForm1 }
function f(x: real): real;
begin
 f := sqr(x) - exp(x) - 2;
end;

procedure TForm1.Button1Click(Sender: TObject);
var
 s: string;
 code: byte;
 c, x, y: real;
begin
 s := InputBox('Введите x', 'Ввод x', '');
 val(s, x, code);
 if code <> 0 then
  begin
   ShowMessage('неверный ввод x');
   exit;
  end;
 s := InputBox('Введите y', 'Ввод y', '');
 val(s, y, code);
 if code <> 0 then
  begin
   ShowMessage('неверный ввод y');
   exit;
  end;
 if f(x) * f(y) > 0 then
   memo1.Lines.Add('Нет корней')
 else
  begin
   repeat
     c := x - (y - x) * f(x) / (f(y) - f(x));
     if f(x) * f(c) > 0 then
       x := c
     else
       y := c;
     Chart1LineSeries1.AddXY(c, f(c), '');
   until abs(f(c)) < e;
   memo1.Lines.Add(floattostr(c));
  end;
end;

procedure TForm1.Button2Click(Sender: TObject);
begin
 Close;
end;

procedure TForm1.Button3Click(Sender: TObject);
var
 s: string;
 code: byte;
 shag: integer;
 a, b, x: real;
begin
 s := InputBox('Введите a', 'Ввод a', '');
 val(s, a, code);
 if code <> 0 then
  begin
   ShowMessage('Неверный ввод x');
   exit;
  end;
 s := InputBox('Введите b', 'Ввод b', '');
 val(s, b, code);
 if code <> 0 then
  begin
   ShowMessage('Неверный ввод y');
   exit;
  end;
  shag := 0;
  repeat
      shag+=1;
      x := (a+b)/2;
      if f(a)*f(x) < 0 then b := x
      else a := x;
      if shag > 100 then
        begin
            memo1.Lines.Add('Невозможно вычислить');
            exit;
        end;
  until abs( f(x) ) < e;
  memo1.Lines.Add(floattostr(x));
end;

end.
