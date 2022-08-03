```SQL
SET NAMES utf8mb4;

SET FOREIGN_KEY_CHECKS = 0;

  

-- ----------------------------

-- Table structure for webinar

-- ----------------------------

---- EL NOMBRE DE LA TABLA ESTARA COMPUESTO POR "webinarAñoMesDia"
---- EJMPLO DE NOMBRE webinar2022Enero01

DROP TABLE IF EXISTS `Nombre`;

CREATE TABLE `Nombre`  (

  constancia_ID int UNSIGNED NOT NULL AUTO_INCREMENT,

  `nombre` varchar(45) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL,

  `aP` varchar(45) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL,

  `aM` varchar(45) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL,

  `correo` varchar(100) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL,

  `fecha` timestamp NOT NULL DEFAULT current_timestamp,

  PRIMARY KEY (`constancia_ID`) USING BTREE,

  UNIQUE INDEX `correo`(`correo`) USING BTREE

) ENGINE = MyISAM AUTO_INCREMENT = 1 CHARACTER SET = latin1 COLLATE = latin1_swedish_ci ROW_FORMAT = Dynamic;

  

SET FOREIGN_KEY_CHECKS = 1;
```
#sql