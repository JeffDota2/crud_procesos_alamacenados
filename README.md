# crud_procesos_alamacenados
create database usuarios;
use usuarios;

create table t_usuarios (id_usuario int auto_increment, 
	cuentanro varchar(150), 
	cedula varchar(150), 
	valor varchar(150), 
	primary key(id_usuario));
ALTER TABLE t_usuarios CONVERT TO CHARACTER SET utf8;


DROP procedure IF EXISTS `sp_mostrar_datos`;

DELIMITER $$
USE `usuarios`$$
CREATE PROCEDURE `sp_mostrar_datos` ()
BEGIN
	select id_usuario,
			cuentanro,
			cedula,
			valor 
	from t_usuarios;
END$$

DELIMITER ;

DROP procedure IF EXISTS `sp_insertar_datos`;

DELIMITER $$
USE `usuarios`$$
CREATE PROCEDURE `sp_insertar_datos` (in cuentanroI varchar(50),
										in cedulaI varchar(50),
                                        in valorI varchar(50))
BEGIN
	insert into t_usuarios (cuentanro,
							cedula,
							valor)
			values (cuentanroI,cedulaI,valorI);
END$$

DELIMITER ;


DROP procedure IF EXISTS `sp_actualizar_datos`;

DELIMITER $$
USE `usuarios`$$
CREATE PROCEDURE `sp_actualizar_datos` (in cuentanroU varchar(50),
										in cedulaU varchar(50),
                                        in valorU varchar(50),
                                        in idUsuarioU int)
BEGIN
	update t_usuarios set cuentanro=cuentanroU,
						cedula=cedulaU,
						valor=valorU
				where id_usuario=idUsuarioU;
END$$

DELIMITER ;


DROP procedure IF EXISTS `sp_eliminar_datos`;

DELIMITER $$
USE `usuarios`$$
CREATE PROCEDURE `sp_eliminar_datos` (in idUsuarioD int)
BEGIN
	delete from t_usuarios 
    where id_usuario=idUsuarioD;
END$$

DELIMITER ;

DROP procedure IF EXISTS `sp_obtener_regJuego`;

DELIMITER $$
USE `usuarios`$$
CREATE PROCEDURE `sp_obtener_regJuego` (in idUsuarioO int)
BEGIN
	select * from t_usuarios where id_usuario=idUsuarioO;
END$$

DELIMITER ;
