-# SSODemo
-Matlab PMU demo
function varargout = SSODemo(varargin)
% SSODEMO MATLAB code for SSODemo.fig
%      SSODEMO, by itself, creates a new SSODEMO or raises the existing
%      singleton*.
%
%      H = SSODEMO returns the handle to a new SSODEMO or the handle to
%      the existing singleton*.
%
%      SSODEMO('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in SSODEMO.M with the given input arguments.
%
%      SSODEMO('Property','Value',...) creates a new SSODEMO or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before SSODemo_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to SSODemo_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help SSODemo
 
% Last Modified by GUIDE v2.5 10-Mar-2015 09:44:26

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @SSODemo_OpeningFcn, ...
                   'gui_OutputFcn',  @SSODemo_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT


% --- Executes just before SSODemo is made visible.
function SSODemo_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to SSODemo (see VARARGIN)



% Choose default command line output for SSODemo
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);
DrawStatic(handles); %draw static with preloaded variables
axes(handles.RotatingPhasor); %select and clear other axes
cla;
axes(handles.TimePhasor);
cla;


% UIWAIT makes SSODemo wait for user response (see UIRESUME)
% uiwait(handles.SSOtag);


% --- Outputs from this function are returned to the command line.
function varargout = SSODemo_OutputFcn(hObject, eventdata, handles) 
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;



function VMag_Callback(hObject, eventdata, handles)
% hObject    handle to VMag (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of VMag as text
%        str2double(get(hObject,'String')) returns contents of VMag as a double


% --- Executes during object creation, after setting all properties.
function VMag_CreateFcn(hObject, eventdata, handles)
% hObject    handle to VMag (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end
x= str2double(get(hObject,'String'));
if (x==0),
    warndlg('Amplitude of phasor may not be zero.  Amplitude set to 1.0','Input Error')
    set(hObject,'String','1.0');
end


function VPhase_Callback(hObject, eventdata, handles)
% hObject    handle to VPhase (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of VPhase as text
%        str2double(get(hObject,'String')) returns contents of VPhase as a double


% --- Executes during object creation, after setting all properties.
function VPhase_CreateFcn(hObject, eventdata, handles)
% hObject    handle to VPhase (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function IMag_Callback(hObject, eventdata, handles)
% hObject    handle to IMag (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of IMag as text
%        str2double(get(hObject,'String')) returns contents of IMag as a double


% --- Executes during object creation, after setting all properties.
function IMag_CreateFcn(hObject, eventdata, handles)
% hObject    handle to IMag (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end
x= str2double(get(hObject,'String'));
if (x==0),
    warndlg('Amplitude of phasor may not be zero.  Amplitude set to 1.0','Input Error')
    set(hObject,'String','1.0');
end


function IPhase_Callback(hObject, eventdata, handles)
% hObject    handle to IPhase (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of IPhase as text
%        str2double(get(hObject,'String')) returns contents of IPhase as a double


% --- Executes during object creation, after setting all properties.
function IPhase_CreateFcn(hObject, eventdata, handles)
% hObject    handle to IPhase (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function ZMag_Callback(hObject, eventdata, handles)
% hObject    handle to ZMag (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of ZMag as text
%        str2double(get(hObject,'String')) returns contents of ZMag as a double


% --- Executes during object creation, after setting all properties.
function ZMag_CreateFcn(hObject, eventdata, handles)
% hObject    handle to ZMag (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end
x= str2double(get(hObject,'String'));
if (x==0),
    warndlg('Amplitude of phasor may not be zero.  Amplitude set to 1.0','Input Error')
    set(hObject,'String','1.0');
end



function ZPhase_Callback(hObject, eventdata, handles)
% hObject    handle to ZPhase (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of ZPhase as text
%        str2double(get(hObject,'String')) returns contents of ZPhase as a double


% --- Executes during object creation, after setting all properties.
function ZPhase_CreateFcn(hObject, eventdata, handles)
% hObject    handle to ZPhase (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function SSO_Callback(hObject, eventdata, handles)
% hObject    handle to SSO (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of SSO as text
%        str2double(get(hObject,'String')) returns contents of SSO as a double


% --- Executes during object creation, after setting all properties.
function SSO_CreateFcn(hObject, eventdata, handles)
% hObject    handle to SSO (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


% --- Executes on button press in Vpress.
function Vpress_Callback(hObject, eventdata, handles)
% hObject    handle to Vpress (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
IMag=str2double(get(handles.IMag,'String'));
IPhase=str2double(get(handles.IPhase,'String'));
ZMag=str2double(get(handles.ZMag,'String'));
ZPhase=str2double(get(handles.ZPhase,'String'));
SSO=str2double(get(handles.SSO,'String'));
VMag=IMag*ZMag;
VPhase=IPhase+ZPhase;
set(handles.VMag,'String',num2str(VMag));
set(handles.VPhase,'String',num2str(VPhase));
DrawStatic(handles);
DrawRotating(handles);


% --- Executes on button press in Ipress.
function Ipress_Callback(hObject, eventdata, handles)
% hObject    handle to Ipress (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
VMag=str2double(get(handles.VMag,'String'));
VPhase=str2double(get(handles.VPhase,'String'));
ZMag=str2double(get(handles.ZMag,'String'));
ZPhase=str2double(get(handles.ZPhase,'String'));
SSO=str2double(get(handles.SSO,'String'));
IMag=VMag/ZMag;
IPhase=VPhase-ZPhase;
set(handles.IMag,'String',num2str(IMag));
set(handles.IPhase,'String',num2str(IPhase));
DrawStatic(handles);
DrawRotating(handles);

% --- Executes on button press in Zpress.
function Zpress_Callback(hObject, eventdata, handles)
% hObject    handle to Zpress (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
IMag=str2double(get(handles.IMag,'String'));
IPhase=str2double(get(handles.IPhase,'String'));
VMag=str2double(get(handles.VMag,'String'));
VPhase=str2double(get(handles.VPhase,'String'));
SSO=str2double(get(handles.SSO,'String'));
ZMag=VMag/IMag;
ZPhase=VPhase-IPhase;
set(handles.ZMag,'String',num2str(ZMag));
set(handles.ZPhase,'String',num2str(ZPhase));
DrawStatic(handles);
DrawRotating(handles);

% --- Executes on button press in HaltToggle.
function HaltToggle_Callback(hObject, eventdata, handles)
% hObject    handle to HaltToggle (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% Hint: get(hObject,'Value') returns toggle state of HaltToggle

% --- Executes on button press in PauseToggle.
function PauseToggle_Callback(hObject, eventdata, handles)
% hObject    handle to PauseToggle (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hint: get(hObject,'Value') returns toggle state of PauseToggle

function Tlength_Callback(hObject, eventdata, handles)
% hObject    handle to Tlength (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of Tlength as text
%        str2double(get(hObject,'String')) returns contents of Tlength as a double


% --- Executes during object creation, after setting all properties.
function Tlength_CreateFcn(hObject, eventdata, handles)
% hObject    handle to Tlength (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function DrawStatic(handles);
%load handle variables into Mag/Phase variables
IMag=str2double(get(handles.IMag,'String'));
IPhase=str2double(get(handles.IPhase,'String'))*pi/180;
ZMag=str2double(get(handles.ZMag,'String'));
ZPhase=str2double(get(handles.ZPhase,'String'))*pi/180;
VMag=str2double(get(handles.VMag,'String'));
VPhase=str2double(get(handles.VPhase,'String'))*pi/180;
%load and clear axes
axes(handles.StaticPhasor);
cla;
%find abs max and set axis size based on it
Gmax=max(max(VMag,ZMag),IMag); 
axis(Gmax*[-1 1 -1 1]);
plotArrow(IMag,IPhase,'b');
plotArrow(ZMag,ZPhase,'m');
plotArrow(VMag,VPhase,'r');

%Draw an Arrowhead and a small circle to show the x-axis intercept).
function plotArrow(A,phi,c)
hold on
%Define Arrow.
x=[0 A A-0.2 A A-0.2]';
y=[0 0 0.2 0 -0.2]';
%Rotate Arrow.
x1=x*cos(phi)-y*sin(phi);
y1=x*sin(phi)+y*cos(phi);
%Plot Arrow.
plot(x1,y1,c,'LineWidth',2)

%Define small circle and plot it on x axis.
theta=0:pi/4:2*pi;
xp=A*cos(phi)+0.1*cos(theta);
yp=0.1*sin(theta);
fill(xp,yp,c,'EdgeColor',c);

%Draw dotted circle to show full phasor path.
theta=0:0.1:2*pi;
plot(A*cos(theta),A*sin(theta),strvcat(c,':'));

function DrawRotating(handles)
IMag=str2double(get(handles.IMag,'String'));
IPhase=str2double(get(handles.IPhase,'String'))*pi/180;
VMag=str2double(get(handles.VMag,'String'));
VPhase=str2double(get(handles.VPhase,'String'))*pi/180;
ZMag=str2double(get(handles.ZMag,'String'));  %ZMag is needed below for scaling figure.
SSO=str2double(get(handles.SSO,'String'));
Tlength=str2double(get(handles.Tlength,'String'));

%f=str2double(get(handles.Frequency,'String'));
%omega=2*pi*f;
f=60;
omega=2*pi*60;
SSOomega=2*pi*SSO;

% t=0:0.1:10;
%t=0:0.01:1;
t=0:0.001:Tlength; 

% set(handles.PauseToggle,'Value',get(handles.PauseToggle,'Min'));
% set(handles.PauseToggle,'String','Pause');

theta=0:pi/4:2*pi;
for i=1:length(t),
    
    
    axes(handles.RotatingPhasor);
    cla;
    grid on;
    
    Gmax=max(max(VMag,ZMag),IMag);
    
    axis(Gmax*[-1 1 -1 1]);
    
    plotArrow(IMag,IPhase+omega*t(i),'b');
    plotArrow(VMag,VPhase+omega*t(i),'r');
    text(-0.8*Gmax, 0.8*Gmax, sprintf('t=%g  ',t(i))); %prints text in the corner
    %}
    
    %Time waveform
    axes(handles.TimePhasor);
    cla;
    grid on;
    hold on;     
    
    %maybe an axis showing 60 Hz w/ no SSO?
    %axis([0 10 -Gmax Gmax]);
    axis([0 Tlength -Gmax Gmax]);
    x=t(1:i);                           % x= time vector, every point up to now
    %y=IMag*cos(IPhase+omega*x);         % y= current wave, blue
    yv=IMag*cos(IPhase+omega*x).*cos(IPhase+SSOomega*x);
    plot(x,yv,'b');
    xp=x(end)+0.0003*Gmax*cos(theta);     % xp/yp= vectors drawing highlight dots 
    yp=yv(end)+0.03*Gmax*sin(theta);     %might need to change based on time scale
    fill(xp,yp,'b','EdgeColor','b');    %draw highlight dot, make edge color same
    %y=VMag*cos(VPhase+omega*x);         % y= voltage wave
    yi=VMag*cos(VPhase+omega*x).*cos(VPhase+SSOomega*x);
    %printvar=(yi(end))
    plot(x,yi,'r');                      
    xp=x(end)+0.0003*Gmax*cos(theta);    % xp= dots for emphasis
    yp=yi(end)+0.03*Gmax*sin(theta);     
    fill(xp,yp,'r','EdgeColor','r');    
    xlabel('Time (s)');
    ylabel('Function value');
    handles=guidata(handles.SSOtag);  %Reload handles (may change on halt or pause button).
    
    pause(.1)                          %add speed function maybe
    
    %{
    axes(handles.RotatingPhasor);
    cla;
    grid on;
    %Gmax=max(max(VMag,ZMag),IMag);
    axis(Gmax*[-1 1 -1 1]);
    

    plotArrow(yi(end),IPhase+omega*t(i),'b');
    plotArrow(yv(end),VPhase+omega*t(i),'r');
    text(-0.8*Gmax, 0.8*Gmax, sprintf('t=%g  ',t(i))); %prints text in the corner
    
    %}
    
    while (get(handles.PauseToggle,'Value')==get(handles.PauseToggle,'Max')),
        pause(0.2); 
        set(handles.PauseToggle,'String','Continue');
    end
    set(handles.PauseToggle,'String','Pause');
    if (get(handles.HaltToggle,'Value')==get(handles.HaltToggle,'Max')),
        set(handles.HaltToggle,'Value',get(handles.HaltToggle,'Min'));
        break
    end

end
