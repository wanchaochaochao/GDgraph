function varargout = exm080201(varargin)
%EXM080201 M-file for exm080201.fig
%      EXM080201, by itself, creates a new EXM080201 or raises the existing
%      singleton*.
%
%      H = EXM080201 returns the handle to a new EXM080201 or the handle to
%      the existing singleton*.
%
%      EXM080201('Property','Value',...) creates a new EXM080201 using the
%      given property value pairs. Unrecognized properties are passed via
%      varargin to exm080201_OpeningFcn.  This calling syntax produces a
%      warning when there is an existing singleton*.
%
%      EXM080201('CALLBACK') and EXM080201('CALLBACK',hObject,...) call the
%      local function named CALLBACK in EXM080201.M with the given input
%      arguments.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help exm080201

% Last Modified by GUIDE v2.5 02-Feb-2015 20:40:37

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @exm080201_OpeningFcn, ...
                   'gui_OutputFcn',  @exm080201_OutputFcn, ...
                   'gui_LayoutFcn',  [], ...
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


% --- Executes just before exm080201 is made visible.
function exm080201_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   unrecognized PropertyName/PropertyValue pairs from the
%            command line (see VARARGIN)
zeta=0.3;
set(handles.edit1,'String',num2str(zeta))
set(handles.slider1,'Value',zeta)
set(handles.gridon,'Value',0)
set(handles.gridoff,'Value',1)
set(handles.listbox1,'Value',1)
handles.t=0:0.05:15;
handles.Color='Red';
handles.zeta=zeta;
handles.flag=0;
handles=surfplot(handles);
handles.flag=1;
handles.Color='Blue';
% Choose default command line output for exm080201
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes exm080201 wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = exm080201_OutputFcn(hObject, eventdata, handles)
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;


% --- Executes on button press in gridon.
function gridon_Callback(hObject, eventdata, handles)
% hObject    handle to gridon (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
set(handles.gridoff,'Value',0)
grid on
% Hint: get(hObject,'Value') returns toggle state of gridon


% --- Executes on selection change in listbox1.
function listbox1_Callback(hObject, eventdata, handles)
% hObject    handle to listbox1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
listindex=get(hObject,'Value');
if any(listindex==1)
    set(handles.listbox1,'Value',1)
end
handles.flag=0;
handles=surfplot(handles);
handles.flag=1;
guidata(hObkect,handles);
% Hints: contents = cellstr(get(hObject,'String')) returns listbox1 contents as cell array
%        contents{get(hObject,'Value')} returns selected item from listbox1


% --- Executes during object creation, after setting all properties.
function listbox1_CreateFcn(hObject, eventdata, handles)
% hObject    handle to listbox1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: listbox controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


% --- Executes on button press in gridoff.
function gridoff_Callback(hObject, eventdata, handles)
% hObject    handle to gridoff (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
set(handles.gridon,'Value',0)
grid off
% Hint: get(hObject,'Value') returns toggle state of gridoff



function edit1_Callback(hObject, eventdata, handles)
% hObject    handle to edit1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
sz=get(hObject,'String');
zeta=str2double(sz);
set(handles.slider1,'Value',zeta)
handles.zeta=zeta;
handles=surfplot(handles);
guidata(hObject,handles);
% Hints: get(hObject,'String') returns contents of edit1 as text
%        str2double(get(hObject,'String')) returns contents of edit1 as a double


% --- Executes during object creation, after setting all properties.
function edit1_CreateFcn(hObject, eventdata, handles)
% hObject    handle to edit1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


% --- Executes on slider movement.
function slider1_Callback(hObject, eventdata, handles)
% hObject    handle to slider1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
zeta=get(hObect,'Value');
set(handles.edit1,'String',num2str(zeta))
handles.zeta=zeta;
handles=surfplot(handles);
guidata(hObject,hndles);
% Hints: get(hObject,'Value') returns position of slider
%        get(hObject,'Min') and get(hObject,'Max') to determine range of slider


% --- Executes during object creation, after setting all properties.
function slider1_CreateFcn(hObject, eventdata, handles)
% hObject    handle to slider1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: slider controls usually have a light gray background.
if isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor',[.9 .9 .9]);
end





function handles=surfplot(handles)
zeta=handles.zeta;
t=handles.t;
listindex=get(handles.listbox1,'Value');
Nt=length(t);
if handles.flag==0
    cla
    zmin=get(handles.slider1,'Min');
    zmax=get(handles.slider1,'Max');
    zt=zmin:0.05:zmax;
    Nz=length(zt);
    [ZT,T]=meshgrid(zt,t);
    Y=zeros(Nt,Nz);
    for k=1:Nz;
        Y(:,k)=step(tf(1,[1,2*zt(k),1]),t);
    end
    surface(ZT,T,Y)
    shading flat
else
    delete(handles.g1)
    delete(handles.rline)
end
xz=ones(1,Nt)*zeta;
y1=ones(1,Nt)*1;
y=step(tf(1,[1,2*zeta,1]),t);
gz=[zeta,zeta,xz,zeta,zeta,xz];
gt=[t(1),t(1),t,t(end),t(end),fliplr(t)];
gy=[0,1,y1,1,0,0*y1];
handles.g1=line(gz,gt,gy,'Color','g','LineWidth',1);
handles.rline=line(xz,t,y,'Color',handles.Color,'LineWidth',2);
K=length(get(handles.listbox1,'Value'));
for jj=1:K
    switch listindex(jj)
        case 1
        case 2
            k95=min(find(y>0.95));k952=[(k95-1),k95];
            t95=interp1(y(k952),t(k952),0.95);
            line(zeta,t95,'Marker','+','Markeredgecolor','k','MarkerSize',6);
        case 3
            [ym,km]=max(y);
            if km<Nt & (ym-1)>0
                line(zeta,t(km),ym,'Marker','.','Markeredgecolor','k','MarkerSize',5);
            end
        case 4
            ii=max(find(abs(y-1)>0.05));
            if ii<Nt
                line(zeta,t(ii+1),y(ii+1),'Color','r','Marker','o','MarkerSize',5)
            end
    end
end
xlabel('{\zeta}')
ylabel('t')
zlabel('y')
alpha(0.7)
view(75,44)