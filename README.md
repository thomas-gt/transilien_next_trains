### Overview of Transilien Next Trains

**Transilien Next Trains is a widget for the awesome [Dashing](http://dashing.io/) (deprecated) or [Smashing](https://github.com/SmashingDashboard/smashing) (active fork) projects.**

It displays the next train departures and status for your favorite train station of **[Transilien](https://www.transilien.com/)**, the main suburban railway network of **[Paris](http://www.paris.fr/)** (around 400 train stations and 14 Lines). Optionaly you can filter trains by adding an Arrival Station to show only a specific journey.
This widget relies on the **[SNCF Open Data Transilien API](http://api.transilien.com/)** and has been tested succesfully for several stations on RER E, RER B, RER D and Paris Saint-Lazare lines.  
<br>
<!-- ![Screenshot #1](https://framapic.org/kapfbgxs4D4g/2WVyAGQat7hU.png) -->
<img src="https://framapic.org/kapfbgxs4D4g/2WVyAGQat7hU.png" width="720">

<br>
### 1. Widget Install Steps

#### 1.1. API Key
Ask for a [personal (free) API key](https://ressources.data.sncf.com/explore/dataset/api-temps-reel-transilien/) and test access with it from Linux command line with curl :

```
$ curl http://api_username:api_password@api.transilien.com/gare/87758607/depart/87681007/
```

#### 1.2. Install nokogiri Library 
Add in your Gemfile :

```
gem 'nokogiri'
```

Then install it :

```
$ sudo bundle install
```

#### 1.3. Download and Unzip or Clone Widget Locally

Directory tree should be like this :

```
.
|-- README.md
|-- CHANGELOG
|-- LICENSE
|-- assets
|   `-- images
|       `-- transilien_next_trains
|           |-- Logo_RER.svg
|           |-- Logo_RER_A.svg
|           |-- Logo_RER_B.svg
|           |-- Logo_RER_C.svg
|           |-- Logo_RER_D.svg
|           |-- Logo_RER_E.svg
|           |-- Logo_SNCF_Transilien.svg
|           |-- Logo_Transilien.svg
|           |-- Logo_Transilien_H.svg
|           |-- Logo_Transilien_J.svg
|           |-- Logo_Transilien_K.svg
|           |-- Logo_Transilien_L.svg
|           |-- Logo_Transilien_N.svg
|           |-- Logo_Transilien_P.svg
|           |-- Logo_Transilien_R.svg
|           `-- Logo_Transilien_U.svg
|-- dashboards
|   `-- transilien_next_trains.erb
|-- jobs
|   `-- transilien_next_trains.rb
`-- widgets
    `-- transilien_next_trains
        |-- transilien_next_trains.coffee
        |-- transilien_next_trains.html
        `-- transilien_next_trains.scss
```

#### 1.4. Move Directories and Files to Corresponding Directories Tree of Personal Install 
<br>
### 2. Widget Setup Steps

#### 2.1. Edit transilien_next_trains.rb File
Configure widget like this :
  - Search the **UIC code** of your favorite station (look at "stations" variable) and set **Departure_Station variable** with it
  - Optionally you can do the same for **Arrival_Station** to filter trains. If you want all trains from departure station let **Arrival_Station=""**
  - Optionally you can change **SCHEDULER refresh interval**. **Default is 60s** (recommended). API allows up to 20 calls/minute but this is useless for a dashboard app. No need to overload API servers.

#### 2.2. Edit transilien_next_trains.html File

Optionally you can change the logo to match the relevant train line of your favorite station. Eg :

```
<img class="logo-line" src="/assets/transilien_next_trains/Logo_Transilien.svg" height="32" width="32">
```
to :
```
<img class="logo-line" src="/assets/transilien_next_trains/Logo_Transilien_P.svg" height="32" width="32">
```
<br>
### 3. Dashboard Setup Steps

#### 3.1. Sample Dashboard 

A demo dashboard is included. If no options is set (token, HTTPS...) pointing browser on [http://your_server:your_port/transilien_next_trains](http://your_server:your_port/transilien_next_trains) should display it after starting server.

#### 3.2. Widget in Custom Dashboard

To add widget put a HTML block like below and customize it, at least data-title, data-sizex and data-sizey values (see previous warning).
**IMPORTANT : Due to high number of information to show up this widget is optimized for 1920x1080 displays, so for a widget_base_dimensions = [370, 340] with data-sizex=2 and data-sizey=1.**

```
<li data-row="1" data-col="1" data-sizex="2" data-sizey="1">
  <div data-id="transilien_next_trains" data-view="TransilienNextTrains" data-unordered="true" data-title="Next Train Departures from My Beautiful Station" data-moreinfo="(R)eal Time - (T)imeTable"></div>
  <i class="fa fa-train icon-background-transilien"></i>
</li>
```
<br>
**Then restart dashing/smashing and enjoy !**
<br>
### Thanks
Got some inspirations to start from [KVB widget](https://gist.github.com/bascht/6081707). Thanks to his [author](https://github.com/bascht).
<br>
### Disclaimer
**THIS SOFTWARE IS PROVIDED "AS IS" AND ANY EXPRESSED OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE AUTHOR OR ITS CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.**
<br>
### License
This widget is licensed under [Creative Commons Attribution-NonCommercial-ShareAlike 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).
<br>![alt Creative Commons Attribution-NonCommercial-ShareAlike 4.0](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png)
