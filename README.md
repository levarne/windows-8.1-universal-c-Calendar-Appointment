# windows-8.1-universal-c-sharp-Calendar-Appointment
Calendar Appointment uses C# WINRT to add appointments to your windows universal app.

Head over to Solution Explorer,

add an existing project, find the project file calendarPlug.csproj

choose the project you on, be it mobile or windows, <this code should work on both platforms>,
Add a reference to the project, by browsing your solution, look for the bin/debug and add the calendarPlug.winmd file.

You should be good to go, bottom you will find a sample on how to use it in javascript

``` javascript
 function addAppointment()
                {
                    var newCalendar = new calendarPlug.CalendarSync();

                    var appointStartTime = new Date("Jun 30, 2015 15:13:00");
                    var appointEndTime = new Date("Jun 30, 2015 19:13:00");
                    var subject = "Time Zone Change to brazil";
                    var details = "This is a Auto add text appointment, did this because an appoinment can only be added through user interaction";
                    var timeZoneStr = "Eastern Standard Time";

                    newCalendar.createAppointment(subject, details, appointStartTime, appointEndTime, timeZoneStr, function (e) {
                        console.log(e);
                    });
                }            
```


NB*** WinRTTimeZones,  package already installed, go into nuget remove this package and add it again, now build the cs project and rebuild your entire 

project, then your good to go.

because store/winrt apps are handicapped in what they can access in the .Net frame work.


================================================================================================


//SIMPLER JAVASCRIPT WAY, BUT YOU CANT CONVERT TIMEZONE WITHOUT LOADING A PLUGIN HAHA
```C#
 appointment.subject = subtitle;
                appointment.details = details;
                appointment.subject = subject;
                appointment.startTime = appointTime;

                Windows.ApplicationModel.Appointments.AppointmentManager.showAddAppointmentAsync(appointment, rect).done(
                                                                                    function (appointmentId) {
                                                                                        if (appointmentId) {
                                                                                            document.querySelector('#result').innerText = "Appointment Id: " 

+ appointmentId;
                                                                                        } else {
                                                                                            document.querySelector('#result').innerText = "Appointment not 

added";
                                                                                        }
                                                                                    });
```
