%NOTE: THIS FILTERS ECG SIGNAL IN ECG.MAT FIILE 
clc;
clear all;
close all;

fs=360;
% PART A- BAND STOP FILTERS
[z1,p1]=butter(3,[49/(fs/2) 51/(fs/2)],'stop'); % 50Hz Filter
[z2,p2]=butter(3,[59/(fs/2) 61/(fs/2)],'stop'); % 60Hz Filter

% PART B
figure(1);
[H1,w1]=freqz(z1,p1);
[H2,w2]=freqz(z2,p2);

subplot(2,1,1);
plot(fs*w1/(2*pi),abs(H1));
ylabel('Magnitude');
title('50Hz band-stop filter');

subplot(2,1,2);
plot(fs*w2/(2*pi),abs(H2));
xlabel('Frequency (Hz)');
title('60Hz band-stop filter');
%
t=(0:511)/fs;
% PART 3
figure(2);
subplot(3,1,1);
del=zeros(1,512); 
del(1,1)=1;     % Discrete Delta Function

x=del; % 'LET'

plot(t,del);
axis([-0.1 1 -1 1]);
title('x(n)= delta(n)');
ylabel('Amplitude');
% Let x(n)= delta(n)
% Let N, Hum Noise = 5sin(2pi(50)t)
% So, y = del + 5sin(2pi(50)t)

N=sin(2*pi*50.*t); % HUM NOISE


y=del+N;  % RECORDED SIGNAL
subplot(3,1,2);
plot(t,y);
axis([-0.1 1 -1 1]);
title('y(n)=x(n)+N(n)=delta(n)+sin(2*pi*50*n)');
% 50 Hz Filtering of recorded signal;
fouriery=abs(freqz(y));
filtered=fouriery.*abs(H1);
xcapt=filter(z1,p1,y);
subplot(3,1,3);
plot(t,xcapt);
axis([-0.1 1 -1 1])
title('xcap(n)= filtered output using 50Hz band-stop');
xlabel('Time(s)');

% PART D ---
figure(3);
subplot(2,2,1);
plot(fs*w1/(2*pi),abs(freqz(x)),'r');
title('Mag. Spectra of x(n)=delta(n)');
ylabel('Magnitude');

subplot(2,2,2);
plot(fs*w1/(2*pi),abs(freqz(y)),'b');
title('Mag. Spectra of y(n)=delta(n)+sin(2pi*50*n)');


subplot(2,2,3);
plot(fs*w1/(2*pi),filtered,'k');
title('Mag. Spectra of 50Hz Filtered from y(n),i.e, xcap(n)');

subplot(2,2,4);
plot(fs*w1/(2*pi),abs(freqz(x)),'r');
hold on
plot(fs*w1/(2*pi),abs(freqz(y)),'b');
hold on
plot(fs*w1/(2*pi),filtered,'k');
title('Overlap');
axis([0 100 0 150]);
xlabel('Freq.(Hz)');

%PART E
load ECG.mat;



figure(4);
subplot(2,2,1);
t1=(0:3599)/fs
plot(t1,ECG);
title('Given ECG Signal in time domain');
xlabel('time');
axis([0 10 -1 1.5]);
grid;
subplot(2,2,2);
plot(fs*w1/(2*pi),abs(freqz(ECG)));
title('Mag. Spectrum of given ECG Signal');
xlabel('freq.(Hz)');

grid;
axis([0 100 0 200]);
subplot(2,2,3);
filteredtimedomain=filter(z2,p2,ECG);

plot(t1,filteredtimedomain);
title('60Hz Filtered ECG Signal in Time Domain');
xlabel('time');
axis([0 10 -1 1.5]);
grid


subplot(2,2,4);
plot(fs*w1/(2*pi),abs(freqz(filteredtimedomain)));
title('Mag. Spectrum of 60Hz Filtered ECG Signal');
xlabel('freq.(Hz)');
grid;

axis([0 100 0 200]);















































































































%----------------------------------------
%B.S.Vineeth <b.vineeth@iitg.ernet.in>
%BTech EP, Class of 2016,NOV 2013, Copyright (c)
%----------------------------------------
