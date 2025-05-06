import 'package:flutter/material.dart';

class BMIResultScreen extends StatelessWidget {
  final double bmi;

  BMIResultScreen({required this.bmi});

  String _getBMICategory(double bmi) {
    if (bmi < 18.5) return "Underweight";
    if (bmi < 24.9) return "Normal";
    if (bmi < 29.9) return "Overweight";
    return "Obese";
  }

  String _getHealthTip(String category) {
    switch (category) {
      case "Underweight":
        return "Try to eat more nutritious foods.";
      case "Normal":
        return "Keep up the good work!";
      case "Overweight":
        return "Consider light exercise and a balanced diet.";
      case "Obese":
        return "Consult a healthcare provider for advice.";
      default:
        return "";
    }
  }

  @override
  Widget build(BuildContext context) {
    final category = _getBMICategory(bmi);
    final tip = _getHealthTip(category);

    return Scaffold(
      appBar: AppBar(title: Text('BMI Result')),
      body: Center(
        child: Padding(
          padding: const EdgeInsets.all(24),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Text(
                'Your BMI',
                style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
              ),
              Text(
                bmi.toStringAsFixed(1),
                style: TextStyle(fontSize: 48, fontWeight: FontWeight.bold),
              ),
              SizedBox(height: 16),
              Text(
                'Category: $category',
                style: TextStyle(fontSize: 22, color: Colors.blueAccent),
              ),
              SizedBox(height: 20),
              Text(
                tip,
                style: TextStyle(fontSize: 18),
                textAlign: TextAlign.center,
              ),
              SizedBox(height: 30),
              ElevatedButton(
                onPressed: () => Navigator.pop(context),
                child: Text('Back'),
              )
            ],
          ),
        ),
      ),
    );
  }
}
