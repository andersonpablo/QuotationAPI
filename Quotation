<?php

/**
 * Current Quotation
 * @author Henrique Schreiner <@hmschreiner>
 * <pre>
 * {
 *  "bovespa": {
 *      "cotacao":"54256",
 *      "variacao":"+0.15" 
 * },
 *  "dolar": {
 *      "cotacao":"2.2300",
 *      "variacao":"+1.69"
 * },
 *  "euro": {
 *      "cotacao":"3.0290",
 *      "variacao":"+0.58"
 *  },
 *  "atualizacao":"31\/10\/13 - 18:13"
 * }
 * </pre>
 */
class Quotation {

    private static $apiUrl = "http://developers.agenciaideias.com.br/cotacoes/json";
    private static $content;

    public static function init() {
        self::$content = file_get_contents(self::$apiUrl);
        self::$content = json_decode(self::$content);
    }

    public static function dolar() {
        self::init();
        return array(
            "quotation" => self::$content->dolar->cotacao,
            "variation" => self::$content->dolar->variacao,
            "status" => self::getVariation(self::$content->dolar->variacao)
        );
    }

    public static function bovespa() {
        self::init();
        return array(
            "quotation" => self::$content->bovespa->cotacao,
            "variation" => self::$content->bovespa->variacao,
            "status" => self::getVariation(self::$content->bovespa->variacao)
        );
    }

    public static function euro() {
        self::init();
        return array(
            "quotation" => self::$content->euro->cotacao,
            "variation" => self::$content->euro->variacao,
            "status" => self::getVariation(self::$content->euro->variacao)
        );
    }

    public static function getVariation($variation) {
        if (strpos($variation, "+")) {
            return "up";
        } else {
            return "down";
        }
    }

}
