# MusicKit

MusicKit is a framework and DSL for manipulating musical abstractions in Swift.

```swift
let C5 = Pitch(midi: 72)
let neapolitan = Major.bII
print(neapolitan(C5))               // [C♯5, E♯5, G♯5]
let G4 = Chroma.G*4
let plagalCadence = [Major.IV, Major.I]
print(plagalCadence * G4)           // [[C5, E5, G5], [G4, B4, D5]]
```

```swift
let V7ofV = HarmonicFunction.create(Scale.Major, degree: 5, chord: Major.V7)
print(V7ofV(C5))                    // [D6, F♯6, A6, C7]
```

```swift
let pitchSet : PitchSet = [Chroma.B*0, Chroma.Cs*2, Chroma.F*3, Chroma.G*4]
print(Chord.name(pitchSet))         // G7♭5/B
```

```swift
let chordNames = sorted(midi.inputChannelToPitchSet.keys).map {
    Chord.name(midi.inputChannelToPitchSet[$0] ?? PitchSet())
}.reduce("", combine: { (a, r) -> String in
    return a + "\n\(r ?? String())"
})
```

**[Framework Overview](/Documentation/FrameworkOverview.md)**

