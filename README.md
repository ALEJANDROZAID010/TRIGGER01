DELIMITER //
CREATE TRIGGER auditoriaVentas AFTER INSERT ON venta
FOR EACH ROW
BEGIN
    INSERT INTO auditventa (usuario, fecha, observacion)
    VALUES (USER(), NOW(), CONCAT('Se realizó una nueva venta con un total de $', NEW.total));
END;
//
DELIMITER ;
