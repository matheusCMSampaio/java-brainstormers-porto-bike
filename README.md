--EX 1
SELECT  EXTRACT(YEAR FROM C.DT_HR_CONSULTA) AS ANO_CONSULTA_RM550657_RM99069,
        EXTRACT(MONTH FROM C.DT_HR_CONSULTA) AS MES_CONSULTA_RM550657_RM99069,
        FP.ID_FORMA_PAGTO AS "Código da forma Pagto CONSULTA RM550657 RM99069", 
        FP.NM_FORMA_PAGTO AS "Nome da forma de PagtoRM550657 RM99069", 
        SUM(C.VL_CONSULTA) AS VALOR_TOTAL_CONSULTA_RM550657_RM99069
    FROM T_RHSTU_CONSULTA C INNER JOIN T_RHSTU_CONSULTA_FORMA_PAGTO CFP ON (C.NR_CONSULTA = CFP.NR_CONSULTA)
    INNER JOIN T_RHSTU_FORMA_PAGAMENTO FP ON (CFP.ID_FORMA_PAGTO = FP.ID_FORMA_PAGTO)
    WHERE fp.nm_forma_pagto = 'Plano de saude' and EXTRACT(YEAR FROM C.DT_HR_CONSULTA) IN (2022, 2023)
        GROUP BY
            EXTRACT(YEAR FROM C.DT_HR_CONSULTA),
            EXTRACT(MONTH FROM C.DT_HR_CONSULTA),
            FP.ID_FORMA_PAGTO,
            FP.NM_FORMA_PAGTO;

--EX 2
CREATE VIEW v_topn_medic_rm550657_rm99069 AS
    SELECT m.id_medicamento AS "Código do Medicamento", 
            m.nm_medicamento AS "NOME_MEDICAMENTO",
            SUM(p.qt_medicamento) AS "QTDE_MEDICAMENTO_RM550657_RM99069"
    FROM T_RHSTU_PRESCICAO_MEDICA P INNER JOIN T_RHSTU_MEDICAMENTO M ON (P.ID_MEDICAMENTO = M.ID_MEDICAMENTO)
    GROUP BY
        m.id_medicamento,
        m.nm_medicamento;

select * from v_topn_medic_rm550657_rm99069;

--EX3
CREATE VIEW v_consulta_diasemana_rm550657_rm99069 AS
    select  c.dt_hr_consulta as DIA_SEMANA,
            c.dt_hr_consulta as "DIA_SEMANA_CONSULTA",
            c.dt_hr_consulta as "HORA_SEMANA_CONSULTA",
            
            
        from t_rhstu_consulta c inner join 

    
