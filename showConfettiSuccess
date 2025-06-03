// Automatic FlutterFlow imports
import "package:bento_design_system_mtd4px/backend/schema/structs/index.dart"
    as bento_design_system_mtd4px_data_schema;
import "package:bento_design_system_mtd4px/backend/schema/enums/enums.dart"
    as bento_design_system_mtd4px_enums;
import 'package:ff_theme/flutter_flow/flutter_flow_theme.dart';
import '/flutter_flow/flutter_flow_util.dart';
import '/custom_code/actions/index.dart'; // Imports other custom actions
import '/flutter_flow/custom_functions.dart'; // Imports custom functions
import 'package:flutter/material.dart';
// Begin custom action code
// DO NOT REMOVE OR MODIFY THE CODE ABOVE!

import 'package:confetti/confetti.dart';
import 'dart:math' as math;

Future<void> showConfettiSuccess(BuildContext context) async {
  // Get screen dimensions
  final size = MediaQuery.of(context).size;
  final screenWidth = size.width;
  final screenHeight = size.height;

  // Calculate number of blast points based on pixels
  final leftRightSources = math.max(2, (screenHeight / 100).round());
  final bottomSources = math.max(2, (screenWidth / 120).round());

  // Create controllers list
  List<ConfettiController> controllers = [];
  List<Widget> confettiWidgets = [];

  // Define greyscale confetti colors
  const confettiColors = [
    Colors.white,
    Color(0xFFE0E0E0),
    Color(0xFF9E9E9E),
    Color(0xFF616161),
    Color(0xFF424242),
    Colors.black,
  ];

  // Create confetti sources for LEFT SIDE
  for (int i = 0; i < leftRightSources; i++) {
    final controller = ConfettiController(duration: const Duration(seconds: 1));
    controllers.add(controller);

    final topPosition = (screenHeight / (leftRightSources + 1)) * (i + 1);

    confettiWidgets.add(
      Positioned(
        left: 0,
        top: topPosition,
        child: ConfettiWidget(
          confettiController: controller,
          blastDirection: 0, // Right
          shouldLoop: false,
          colors: confettiColors,
          numberOfParticles: 8,
          maxBlastForce: 10,
          minBlastForce: 2,
          emissionFrequency: 0.05,
          gravity: 0.3,
        ),
      ),
    );
  }

  // Create confetti sources for RIGHT SIDE
  for (int i = 0; i < leftRightSources; i++) {
    final controller = ConfettiController(duration: const Duration(seconds: 1));
    controllers.add(controller);

    final topPosition = (screenHeight / (leftRightSources + 1)) * (i + 1);

    confettiWidgets.add(
      Positioned(
        right: 0,
        top: topPosition,
        child: ConfettiWidget(
          confettiController: controller,
          blastDirection: math.pi, // Left
          shouldLoop: false,
          colors: confettiColors,
          numberOfParticles: 8,
          maxBlastForce: 10,
          minBlastForce: 2,
          emissionFrequency: 0.05,
          gravity: 0.3,
        ),
      ),
    );
  }

  // Create confetti sources for BOTTOM SIDE
  for (int i = 0; i < bottomSources; i++) {
    final controller = ConfettiController(duration: const Duration(seconds: 1));
    controllers.add(controller);

    final leftPosition = (screenWidth / (bottomSources + 1)) * (i + 1);

    confettiWidgets.add(
      Positioned(
        bottom: 0,
        left: leftPosition,
        child: ConfettiWidget(
          confettiController: controller,
          blastDirection: -math.pi / 2, // Up
          shouldLoop: false,
          colors: confettiColors,
          numberOfParticles: 8,
          maxBlastForce: 7,
          minBlastForce: 2,
          emissionFrequency: 0.04,
          gravity: 0.3,
        ),
      ),
    );
  }

  // Start all confetti animations immediately
  for (var controller in controllers) {
    controller.play();
  }

  // Show the confetti dialog
  showDialog(
    context: context,
    barrierDismissible: false,
    barrierColor: Colors.transparent,
    builder: (BuildContext context) {
      return Material(
        color: Colors.transparent,
        child: Stack(
          children: confettiWidgets,
        ),
      );
    },
  );

  // Wait for confetti to finish
  await Future.delayed(Duration(seconds: 3));

  // Dismiss the dialog
  if (Navigator.canPop(context)) {
    Navigator.of(context).pop();
  }

  // Dispose controllers
  for (var controller in controllers) {
    controller.dispose();
  }
}
