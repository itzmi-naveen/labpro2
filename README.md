# labpro2
from bokeh.io import show
from bokeh.models import ColumnDataSource, HoverTool
from bokeh.plotting import figure
from bokeh.layouts import column
import pandas as pd
import folium
data = pd.read_csv(r'C:\Users\Naveen\Downloads\cities.csv.zip')
p = figure(width=800, height=400, tools='pan,wheel_zoom,reset')
source = ColumnDataSource(data)
p.circle(x='longitude', y='latitude', size=10, source=source, color='orange')
hover = HoverTool()
hover.tooltips = [("Info", "@country_name"), ("latitude", "@latitude"), ("longitude", "@longitude")]
p.add_tools(hover)
layout = column(p)
show(layout)
m = folium.Map(location=[latitude, longitude], zoom_start=10)
for index, row in data.iterrows():
    folium.Marker(
        location=[row['Latitude'], row['Longitude']],
        popup=row['Info'],  # Display additional info on mouse click
    ).add_to(m)
m.save('map.html')
![Screenshot 2024-09-11 201739](https://github.com/user-attachments/assets/977a6b47-ba46-4757-b729-820fc710d830)
![Screenshot 2024-09-11 202043](https://github.com/user-attachments/assets/d7a629a5-d09a-4f5e-89d4-0ddaec806efd)

