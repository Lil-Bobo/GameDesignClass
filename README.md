# GameDesignClass
My apps, welcome!
//  ContentView.swift
//  AdventureGame
//  Created by Yunting Yin on 6/16/25.

import SwiftUI
struct ContentView: View {
    // Game state
    @State private var currentStep = "start"
    var body: some View {
        VStack(spacing: 20) {
            Spacer()
            switch currentStep {
            case "start":
                Text("Good Morning, what do you do?🛏️")
                HStack {
                    gameButton("Wake Up") {
                        currentStep = "wake"
                    }
                    gameButton("Sleep for 5 more minutes") {
                        currentStep = "sleep"
                    }
                }
            case "sleep":
                Text("You woke up 5 minutes later🥱")
                    .multilineTextAlignment(.center)
                    gameButton("Good morning again!") {
                        currentStep = "start"
                    }

            case "wake":
                Text("😴 You get up, you...")
                    .multilineTextAlignment(.center)
                HStack {
                    gameButton("Shower") {
                        currentStep = "wash"
                    }
                    gameButton("Don't Shower") {
                        currentStep = "noWash"
                    }
                }
            case "wash":
                Text("You only have time to clean one thing because you are late!!!🌞")
                    .multilineTextAlignment(.center)
                HStack {
                    gameButton("Clean Hair") {
                        currentStep = "noWash"
                    }
                    gameButton("Clean Body") {
                        currentStep = "late"
                    }
                }
            case "noWash":
                Text("You are hungry, do you want to have breakfast?🥞🧇🍩")
                HStack {
                    gameButton("Have breakfast") {
                        currentStep = "late"
                    }
                    gameButton("Don't have breakfast") {
                        currentStep = "school"
                    }
                }
            case "late":
                    Text("You took too long, now you are late to school🏫")
                        gameButton("Go to school late") {
                            currentStep = "school"
                        }
            case "school":
                Text("You are finally at school! You have a good day, lets hope tomorrow is better.✏️")
                gameButton("Go to sleep") {
                    currentStep = "start"
                }
            default:
                Text("Game Over.")
            }
            Spacer()
        }
        .padding()
        .font(.title3)
    }
    // Reusable styled button
    func gameButton(_ label: String, action: @escaping () -> Void) -> some View {
        Button(action: action) {
            Text(label)
                .padding(30)
                .frame(maxWidth: .infinity)
                .background(Color.green
                    .opacity(0.8))
                .foregroundColor(.white)
                .cornerRadius(15)
        }
    }
}
#Preview {
    ContentView()
}
