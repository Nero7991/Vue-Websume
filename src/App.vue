<template>
  <div id="app">
    <vue-headful
            title="Oren Collaco"
            description="Oren Collaco's stuff. Have a look around"
            :image="require (`@/assets/logo.png`)"
        />
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <CustomNav Name="Oren Collaco" ProfileURL="oren.jpg" 
    v-bind:MainContent =  '{ 
      Items: [
        {
            "Title": "About",
            "Id": "about",
            "ContentText": "I like designing electronics products and writing code that enables users to accomplish a task or make it easier. The whole world of electronics and computers fasinating to me as it allows one to realise something they have in their minds. I think of them as tools that can be used to make ideas I have in my mind into something real. I like collecting equipment from friends and family who have no use for them. Over the years, I have being adding to my wannabe-electronics lab, and currently it seems to live true to the definition of a electronics lab which has helped me to experiment on things and different kinds of technologies",
            SubItems: [
            {
              Id: "about-labpics",
              Title: "",
              Subtitle: "",
              ContentText: "",
              ImageCount: 2,
              ImageText: "Electronics Lab"
              }

            ]
        },
        {
            "Title": "Projects",
            "Id": "projects", 
            "ContentText":"",
            SubItems: [
            {
              Id: "projects-watch",
              Title: "OLED Wrist Watch",
              Subtitle: "Wrist Watch based on ATmega328P microcontroller using OLED display • Personal Project",
              ContentText: "Started this project as a way to test my abilities and learn from the mistakes that will undoubtedly be made while working on this project. Designing a watch from almost the ground up is a pretty tough task and many challenges were encountered in the process. Decided to use an OLED display as it consumer lower power depending on the number of pixels lit. Used the familiar ATmega328P microcontroller as it provided with the required low power modes, Pin state change interrupts, I2C interface and Real Time Clock(RTC). After few months of debugging of hardware and software side of project, the basic project was realised. The watch worked pretty well although looked hideous relative to a normal watch. In time, issues were found and fixed but the overall project was a huge success and many things were learned in the process.",
              ImageCount: 5
            },
            {
              Id: "projects-wavegen",
              Title: "WaveGen",
              Subtitle: "Waveform generator based on Spartan 3 FPGA • 3rd Year Mini Project",
              ContentText: "We decided to work on FPGA as we had heard about its enormous potential but never got he opportunity to work on it. FPGAs can be to perform multiple computations in parallel and very high speed. They are used in custom solutions that deal with huge streams of data like high resolution video footage. The project we implemented could generate sine, triangle and square waveforms using Spartan 3 FPGA. DAC with 8-bit resolution and sampling rate of 5MHz(The settling time is 100ns) is used to generate the analog signals.",
              ImageCount: 5
            },
            {
              Id: "projects-quadcontroller",
              Title: "Quadcopter Controller Design",
              Subtitle: "Quadcopter controller design using Bluetooth and ATmega328P microcontroller • 3rd Year Mini Project",
              ContentText: "The project helped us to test our ability to design a PCB from scratch using a mix of Surface mount and Through-hole components and to write working code that would be able to dynamically adjust motor speed to stabilize the quadcopter based on sensor data(MP6050). A 4.2V lithium battery that can supply 4A current is used to power the quadcopter, including microcontroller power, MPU6050 sensor power and the motors. Atmega328P microcontroller on this board runs at 1MHz, and can easily process data from MPU6050 to get board orientation. The motors pull huge current if started all at once with full speed, causing voltage dips and restarting the microcontroller. We mitigated this in the firmware by suppressing sudden speeding up of all 4 motors and added decoupling capacitors for all digital components.",
              ImageCount: 2
            },
            {
              Id: "projects-inconard",
              Title: "inConard",
              Subtitle: "IoT Mains power board based on ESP8266 WiFi Module and nRF24L01 transceiver • Final Year Project",
              ContentText: "Allows automation of large warehouse and halls. Uses battery powered wireless sensor to communicate with a central board to turn on/off appliances. The WiFi module (ESP8266) connects to the WiFi network it is configured to connect to on boot up. If the WiFi network has internet available, it tries to connect to the server. On successful connection with the server, it keeps listening to commands from the server. Any ON or OFF command from the server is sent to the microcontroller. The microcontroller (ATmega328P) has direct control over the TRIAC, thus can control the power to any socket. It uses interrupts on the pins connected to the buttons on the board to manually control the sockets. ESP8266, transceiver and the microcontroller communicate using SPI. The microcontroller continuously checks the transceiver for data from the wireless sensors. If relevant data is found, the configured socket is toggled.", 
              ImageCount: 5
            },
            {
              Id: "projects-rc",
              Title: "Speed Controlled Remote Vehicle with On-board Accelerometer and gyroscope",
              Subtitle: "RC vehicle with fine speed control on ATmega328P and nRF24L01 transceiver • Personal Project",
              ContentText: "Designed controller for remote controlled car that allowed minute speed in 256 steps of speed increments. Using the built in timers on the microcontroller that provides 2 independent PWM channels, speed control is implemented. On board ADC is used to provide battery level functionality. nRF24L01 tranceiver enables bidirectional communication between the remote and the vehicle.  The remote vehicle communicates back to the remote giving crucial information like battery level, etc. Uses PWM based on the aforementioned timer to control the speed of the drive motor in 256 steps for forward and backward. A OLED display on the remote displays necessary information", 
              ImageCount: 6
            }
            ]
        },
        {
            "Title": "Experience",
            "Id": "experience", 
            "ContentText":"",
            SubItems: [
            {
              Id: "experience-konnect",
              Title: "Konnect Insights",
              Subtitle: "Software Developer • 6 Months",
              ContentText: "Part of the team tasked with refreshing and adding competitve features to the existing Publish module. Publish module allowed clients to schedule posts to major social media platforms like Twitter, Facebook, Instagram and LinkedIn. Specially tasked with adding features to the compose box in the Publish module such as multiple tabs allowing easier flow while composing posts, implementation of mentions for Facebook and Twitter, built in link shortening, and more. Implemented the backend required to support the addition of the mentioned features. ASP.NET was used as the backend web application framework, with database requirements meet by Microsoft SQL Server. The refreshed Publish module was overall praised by the clients for making the workflow for composing posts easier. The new design crafted by the team was received very postively." 
            },
            {
              Id: "experience-some",
              Title: "Some company",
              Subtitle: "6 Months",
              IsDisplayed: false
            }
            ]
        },
        {
            "Title": "Education",
            "Id": "education",
            "ContentText":"",
            SubItems: 
            [ 
              {
              Id: "education-tb",
              Title: "Thomas Baptista Junior College • 83.85%",
              Subtitle: "Computer Science • 2014"
              },
              {
              Id: "education-agnel",
              Title: "Fr. Conceicao Rodrigues College Of Engineering • 6.75 CGPA",
              Subtitle: "Bachelor Of Engineering in Electronics • 2019"
              }
            ]
        },
        {
            "Title": "Skills",
            "Id": "skills",
            "ContentText":"",
            SubItems: 
            [ 
            {
              Id: "skill-1",
              Title: "",
              Subtitle: " ",
              ContentText: " "
              },
              {
              Id: "skill-2",
              Title: "",
              Subtitle: "Programming: C, C++, Java, HTML, CSS, Python",
              ContentText: ""
              },
              {
              Id: "skill-3",
              Title: "",
              Subtitle: "Hardware Skills: Verilog, System Verilog, Embedded C, Assembly Language",
              ContentText: "",
              IsDisplayed: true
              },
              {
              Id: "skill-4",
              Title: "",
              Subtitle: "Electronic circuits and Integrated circuits design",
              ContentText: "",
              IsDisplayed: true
              },
              {
              Id: "skill-5",
              Title: "",
              Subtitle: "Reading device datasheets and searching for parts that fit the design",
              ContentText: "",
              IsDisplayed: true
              }
              
            ]
        },
        {
            "Title": "Interests",
            "Id": "interests",
            "ContentText":"",
            SubItems: 
            [ 
            {
              Id: "interest-1",
              Title: "",
              Subtitle: " ",
              ContentText: " "
              },
              {
              Id: "interest-2",
              Title: "",
              Subtitle: "Embedded Electronics",
              ContentText: ""
              },
              {
              Id: "interest-3",
              Title: "",
              Subtitle: "IoT based Automation",
              ContentText: "",
              IsDisplayed: true
              },
              {
              Id: "interest-4",
              Title: "",
              Subtitle: "Application Specific Integrated Design(ASIC) Design",
              ContentText: "",
              IsDisplayed: true
              },
              {
              Id: "interest-5",
              Title: "",
              Subtitle: "FPGA Design",
              ContentText: "",
              IsDisplayed: true
              },
              {
              Id: "interest-6",
              Title: "",
              Subtitle: "Digital Signal Processing",
              ContentText: "",
              IsDisplayed: true
              }

            ]
        }
    ]
}'
    />
  </div>
</template>

<script>
import CustomNav from './components/CustomNav.vue'
import vueHeadful from 'vue-headful';
import Vue from "vue";


Vue.component('vue-headful', vueHeadful);



export default {
  name: 'app',
  components: {
    CustomNav
  }
}

</script>

