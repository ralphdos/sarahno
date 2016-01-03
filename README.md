import VPlay 2.0
import QtQuick 2.0

GameWindow {
    id: gameWindow

    // You get free licenseKeys from http://v-play.net/licenseKey
    // With a licenseKey you can:
    //  * Publish your games & apps for the app stores
    //  * Remove the V-Play Splash Screen or set a custom one (available with the Pro Licenses)
    //  * Add plugins to monetize, analyze & improve your apps (available with the Pro Licenses)
    //licenseKey: "<generate one from http://v-play.net/licenseKey>"

    activeScene: scene

    // the size of the Window can be changed at runtime by pressing Ctrl (or Cmd on Mac) + the number keys 1-8
    // the content of the logical scene size (480x320 for landscape mode by default) gets scaled to the window size based on the scaleMode
    // you can set this size to any resolution you would like your project to start with, most of the times the one of your main target device
    // this resolution is for iPhone 4 & iPhone 4S
    width: 960
    height: 640

    Scene {
        id: scene

        // the "logical size" - the scene content is auto-scaled to match the GameWindow size
        width: 960
        height: 640

        // background rectangle matching the logical scene size (= safe zone available on all devices)
        // see here for more details on content scaling and safe zone: http://v-play.net/doc/vplay-different-screen-sizes/

        Rectangle {
            id: rectangle
            anchors.fill: parent
            color: "grey"

            Text {
                id: textElement
                // qsTr() uses the internationalization feature for multi-language support
                text: qsTr("Start")
                font.family: "Viner Hand ITC"
                font.bold: true
                font.pointSize: 12
                smooth: true
                horizontalAlignment: Text.AlignHCenter
                color: "#ffffff"
                anchors.horizontalCenter: parent.horizontalCenter
                anchors.bottom: parent.bottom
                anchors.bottomMargin: 240

            }

            MouseArea {
                anchors.fill: textElement

                // when the rectangle that fits the whole scene is pressed, change the background color and the text
                onPressed: {
                    textElement.text = qsTr("Hello!")
                    rectangle.color = "black"
                    return1.visible = !return1.visible


                    console.debug("pressed position:", mouse.x, mouse.y)
                }

                // revert the text & color after the touch/mouse button was released
                // also States could be used for that - search for "QML States" in the doc


            }

            Text {
                id: return1
                text: qsTr("Back")
                color: "white"
                font.family: "Viner hand ITC"
                font.bold: true
                font.pointSize: 12
                smooth: true
                anchors.bottom: parent.bottom
                anchors.left: parent.left
                visible: false
                
           MouseArea {
               anchors.fill: return1

               onPressed: {
                   return1.visible = !return1.visible
                   rectangle.color = "grey"
                   textElement.text = qsTr("Start")

               }
               }
            }
        }// Rectangle with size of logical scene
