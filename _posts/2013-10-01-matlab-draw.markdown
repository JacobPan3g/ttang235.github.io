---
layout: post
title: Create a Beautiful Bar Graph with Text Label Using Matlab
categories: utilities
---
I need a bar graph with text labels, not numbers. So I searched, and found [this](http://www.mathworks.cn/support/solutions/en/data/1-15TK6/). I made some minor revisions, and got a figure like this:
<img src="/images/2013-10-01-barGraph.png" alt="a pretty bar graph">


The code is given below. Feel free to use it.

```matlab
f=[578.047,2.375,16.609,102.172,2.375,304.61,68.39];
x = 1:length(f);

% Plot the data.
h = bar(x,f);

% Reduce the size of the axis so that all the labels fit in the figure.
pos = get(gca,'Position');
set(gca,'Position',[pos(1), .2, pos(3) .65])

% Add a title, if you need it.
%title('')

% Set X-tick positions
Xt = x;

% If you want to set x-axis limit, uncomment the following two lines of 
% code and remove the third
%Xl = [1 6]; 
%set(gca,'XTick',Xt,'XLim',Xl);
set(gca,'XTick',Xt);
% ensure that each string is of the same length, using leading spaces
algos = ['       CELF'; 'DegDiscount'; '    GroupPR';
    '     Linear'; '     OutDeg'; '   PageRank'; ' buildGraph'];

ax = axis; % Current axis limits
axis(axis); % Set the axis limit modes (e.g. XLimMode) to manual
Yl = ax(3:4); % Y-axis limits

% Remove the default labels
set(gca,'XTickLabel','')

% Place the text labels
t = text(Xt,Yl(1)*ones(1,length(Xt)),algos(1:length(f),:));
set(t,'HorizontalAlignment','right','VerticalAlignment','top', ...
'Rotation',45, 'Fontsize', 13);
ylabel('Running Time/s', 'Fontsize', 13)

%% you don't have to run the following lines, if you don't need xlabel
% Get the Extent of each text object. This
% loop is unavoidable.
for i = 1:length(t)
ext(i,:) = get(t(i),'Extent');
end

% Determine the lowest point. The X-label will be
% placed so that the top is aligned with this point.
LowYPoint = min(ext(:,2));

% Place the axis label at this point
XMidPoint = Xl(1)+abs(diff(Xl))/2;
tl = text(XMidPoint,LowYPoint,'X-Axis Label', ...
'VerticalAlignment','top', ...
'HorizontalAlignment','center');
```

I would recommend you execute those lines one by one to understand what each line is for. And, you may want to have a look at what the original file is like. It could also help you to understand the code.

ps: When inserting matlab code, use *\`\`\`matlab*, instead of *\`\`\`Matlab*. Otherwise, you would get disappointing 'Page Build Failure' message and have a hard time to debug, like me.
