```sql


SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";



-- --------------------------------------------------------

--
-- Table structure for table `webinar2022julio14`
--

CREATE TABLE `nombre` (
  `constancia_ID` int UNSIGNED NOT NULL,
  `nombre` varchar(45) CHARACTER SET latin1 COLLATE latin1_swedish_ci DEFAULT NULL,
  `aP` varchar(45) CHARACTER SET latin1 COLLATE latin1_swedish_ci DEFAULT NULL,
  `aM` varchar(45) CHARACTER SET latin1 COLLATE latin1_swedish_ci DEFAULT NULL,
  `correo` varchar(100) CHARACTER SET latin1 COLLATE latin1_swedish_ci DEFAULT NULL,
  `fecha` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP
) ENGINE=MyISAM DEFAULT CHARSET=latin1 ROW_FORMAT=DYNAMIC;


ALTER TABLE `nombre`
  ADD PRIMARY KEY (`constancia_ID`) USING BTREE,
  ADD UNIQUE KEY `correo` (`correo`) USING BTREE;

--
-- AUTO_INCREMENT for table `nombre`
--
ALTER TABLE `nombre`
  MODIFY `constancia_ID` int UNSIGNED NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=1;
COMMIT;


```
#sql